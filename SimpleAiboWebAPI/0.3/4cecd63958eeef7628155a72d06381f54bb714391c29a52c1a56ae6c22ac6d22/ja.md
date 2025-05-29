```
askApproachObject(
  targetType="pinkball";
  enqueue=false,
  target_deviceID=nothing,
  target_nickname=nothing,
  timeoutLimit=10)
```

`approach_object`に尋ねます。

  * `targetType` : 次の定数のいずれか：

      * `aibo`
      * `aibone`
      * `dice`
      * `pinkball`

このメソッドは、`askAction("approach_object", Dict(TargetType=>targetType, Enqueue=>enqueue))`と同等です。
