```
send_soft_trigger(id::Integer, start::ASI_BOOL)
```

From original docs: Send a softTrigger. For edge trigger, it only need to set true which means send a rising trigger to start exposure. For level trigger, it need to set true first means start exposure, and set false means stop exposure. Only needed to call when the IsTriggerCam in the CameraInfo is true.
