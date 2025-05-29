```
askStay(;
  duration=60,
  enqueue=false,
  target_deviceID=nothing,
  target_nickname=nothing,
  timeoutLimit=10)
```

`duration` 秒間 `stay` を要求します。

  * `duration` : 0–360 (秒)

このメソッドは `askAction("stay", Dict(Duration=>duration, Enqueue=>enqueue))` と同等です。
