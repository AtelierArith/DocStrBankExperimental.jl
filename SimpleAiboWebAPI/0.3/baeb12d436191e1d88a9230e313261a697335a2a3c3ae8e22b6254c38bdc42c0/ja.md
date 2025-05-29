```
askReleaseObject(
  targetType="aibone";
  enqueue=false,
  target_deviceID=nothing,
  target_nickname=nothing,
  timeoutLimit=10)
```

`release_object`を要求します。

  * `targetType` : 次の定数のいずれか：

      * `aibone`
      * `dice`

このメソッドは、`askAction("release_object", Dict(TargetType=>targetType, Enqueue=>enqueue))`と同等です。
