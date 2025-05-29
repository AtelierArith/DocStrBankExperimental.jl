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

`move_head`を要求します。

  * `azimuth` : -80 – 80 (度)
  * `elevation` : -40 – 40 (度)
  * `velocity` : 10 – 80 (度/秒)

このメソッドは、`askAction("move_head", Dict(Duration=>duration, Enqueue=>enqueue))`と同等です。
