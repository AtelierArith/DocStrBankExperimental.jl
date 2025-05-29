```
askMoveHead(;
  azimuth=0,
  elevation=0,
  velocity=0,
  enqueue=false,
  target_deviceID=nothing,
  target_nickname=nothing,
  timeoutLimit=10)
```

asks `move_head`.

  * `azimuth` : -80 – 80 (degree)
  * `elevation` : -40 – 40 (degree)
  * `velocity` : 10 – 80 (deg/sec)

This method is equivalent to `askAction("move_head", Dict(Duration=>duration, Enqueue=>enqueue))`
