```
askKickObject(
  targetType="pinkball";
  kickMotion="kick",
  enqueue=false,
  target_deviceID=nothing,
  target_nickname=nothing,
  timeoutLimit=10)
```

asks `kick_object`.

  * `targetType` : one of the following constants:

      * `pinkball`
  * `kickMotion` : one of the following constants:

      * `kick`
      * `heading`

This method is equivalent to `askAction("kick_object", Dict(TargetType=>targetType, KickMotion=>kickMotion, Enqueue=>enqueue))`
