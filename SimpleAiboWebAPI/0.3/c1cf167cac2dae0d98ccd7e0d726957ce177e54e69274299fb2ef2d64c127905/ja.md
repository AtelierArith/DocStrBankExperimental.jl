```
askChaseObject(
  targetType="pinkball";
  chasingDurationMsec=30*1000,
  enqueue=false,
  target_deviceID=nothing,
  target_nickname=nothing,
  timeoutLimit=10)
```

asks `chase_object`.

  * `targetType` : 次の定数のいずれか：

      * `aibo`
      * `aibone`
      * `dice`
      * `pinkball`
  * `chasingDurationMsec` : 0 – 360000（ミリ秒）

このメソッドは `askAction("chase_object", Dict(TargetType=>targetType, ChasingDurationMsec=> chasingDurationMsec, Enqueue=>enqueue))` と同等です。
