```Julia
wait(interrupt::XRT.XRTWrap.IPInterrupt)
wait(interrupt::XRT.XRTWrap.IPInterrupt, timeout::Integer) -> XRT.XRTWrap.CVStatus.Type

```

Wait for interrupt from IP or for the specified timeout to expire. 
