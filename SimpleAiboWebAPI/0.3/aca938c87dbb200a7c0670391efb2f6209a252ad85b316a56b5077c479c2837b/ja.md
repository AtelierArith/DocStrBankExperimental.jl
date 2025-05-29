```
askFindObject(
  targetType="pinkball";
  enqueue=false,
  target_deviceID=nothing,
  target_nickname=nothing,
  timeoutLimit=10)
```

`find_object`を要求します。

  * `targetType` : 次の定数のいずれか：

      * `aibo`
      * `aibone`
      * `dice`
      * `pinkball`

このメソッドは、`askAction("find_object", Dict(TargetType=>targetType, Enqueue=>enqueue))`と同等です。
