```
askKickObject(
  targetType="pinkball";
  kickMotion="kick",
  enqueue=false,
  target_deviceID=nothing,
  target_nickname=nothing,
  timeoutLimit=10)
```

は `kick_object` を要求します。

  * `targetType` : 次の定数のいずれか：

      * `pinkball`
  * `kickMotion` : 次の定数のいずれか：

      * `kick`
      * `heading`

このメソッドは `askAction("kick_object", Dict(TargetType=>targetType, KickMotion=>kickMotion, Enqueue=>enqueue))` と同等です。
