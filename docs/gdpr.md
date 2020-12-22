# Tracking Consent

### Tracking consent values

In order to be compliant with the GDPR regulation the SDK needs requires the tracking consent value at initialization.
The tracking consent can have one of the values:

1. `TrackingConsent.PENDING` - the SDK will start collecting and batching the data but will not send it to the data 
   collection endpoint. It will wait for the new tracking consent value to decide what to do with the batched data.
2. `TrackingConsent.GRANTED` - the SDK will start collecting the data and will be sending it to the data collection endpoint.
3. `TrackingConsent.NOT_GRANTED` - the SDK will not collect any data. You will not be able to manually send any logs, traces or 
   RUM events.
   
### Updating the tracking consent at runtime

If you want to update the tracking consent after the SDK was initialized you can do so by calling: `Datadog.setTrackingConsent(<NEW CONSENT>)`.
The SDK will change its behaviour according with the new consent. For example if the current tracking consent is `TrackingConsent.PENDING` and we update it to:

1.  `TrackingConsent.GRANTED`  - the SDK will send all the batched data and from now on all the data will be sent directly to the data collection endpoint.
2. `TrackingConsent.NOT_GRANTED`  - the SDK will wipe all the batched data and from now on will not collect any data.