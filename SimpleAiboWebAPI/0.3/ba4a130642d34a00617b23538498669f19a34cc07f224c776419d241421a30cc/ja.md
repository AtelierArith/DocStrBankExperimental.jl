```
askGetCloseToObject(
  targetType="pinkball";
  distance=0.2,
  enqueue=false,
  target_deviceID=nothing,
  target_nickname=nothing,
  timeoutLimit=10)
```

`get_close_to_object`を要求します。このメソッドは`askApproachObject`の後に呼び出してください。

  * `targetType` : 次の定数のいずれか：

      * `aibo`
      * `aibone`
      * `dice`
      * `pinkball`
  * `distance` : 0.1 – 0.3 (メートル)

このメソッドは`askAction("get_close_to_object", Dict(TargetType=>targetType, Distance=>distance, Enqueue=>enqueue))`と同等です。
