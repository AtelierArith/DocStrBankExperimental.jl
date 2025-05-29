```
askExplore(
  duration=60;
  enqueue=false,
  target_deviceID=nothing,
  target_nickname=nothing,
  timeoutLimit=10)
```

`explore`を要求します。

  * `duration` : 0 – 360 (秒)

このメソッドは、`askAction("explore", Dict(Duration=>duration, Enqueue=>enqueue))`と同等です。
