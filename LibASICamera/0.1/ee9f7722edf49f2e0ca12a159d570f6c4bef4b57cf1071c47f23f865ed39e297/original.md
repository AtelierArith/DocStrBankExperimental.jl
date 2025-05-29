```
set_trigger_output_config(id::Integer, pin::ASI_TRIG_OUTPUT_PIN, high::ASI_BOOL, delay, duration)
```

Configure the output pin (A or B) of Trigger port. If duration <= 0, this output pin will be closed. Only need to call when the IsTriggerCam in the CameraInfo is true.

# Args:

```
id: Camera id
pin: Select the pin for output
high: If true, the selected pin will output a high level as a signal
				when it is effective.
delay: The delay between the camera receiving a trigger signal and the
        output of the valid level. From 0 μs - 2,000,000,000 μs.
duration: The duration of the valid level output. Same range as delay.
```
