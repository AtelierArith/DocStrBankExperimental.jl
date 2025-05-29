```
askStay(;
  duration=60,
  enqueue=false,
  target_deviceID=nothing,
  target_nickname=nothing,
  timeoutLimit=10)
```

asks `stay` for `duration` seconds.

  * `duration` : 0–360 (seconds)

This method is equivalent to `askAction("stay", Dict(Duration=>duration, Enqueue=>enqueue))`
