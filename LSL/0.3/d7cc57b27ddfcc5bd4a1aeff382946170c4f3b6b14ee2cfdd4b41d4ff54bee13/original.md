```
local_clock()
```

Return local system time stamp in seconds.

The resolution is better than a milisecond. This reading can be used to assign time stamps to samples as they are being acquired. If the "age" of a sample is known at a particular time (e.g., from USB transmission delays), it can be used as an offset to local*clock() to  obtain a better estimate of when a sample was actually captured. See push*sample() for a use case.
