```
askExplore(
  duration=60;
  enqueue=false,
  target_deviceID=nothing,
  target_nickname=nothing,
  timeoutLimit=10)
```

asks `explore`.

  * `duration` : 0 – 360 (seconds)

This method is equivalent to `askAction("explore", Dict(Duration=>duration, Enqueue=>enqueue))`
