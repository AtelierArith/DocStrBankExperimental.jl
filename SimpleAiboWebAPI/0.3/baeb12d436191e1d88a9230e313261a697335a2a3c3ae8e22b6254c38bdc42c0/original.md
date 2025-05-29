```
askReleaseObject(
  targetType="aibone";
  enqueue=false,
  target_deviceID=nothing,
  target_nickname=nothing,
  timeoutLimit=10)
```

asks `release_object`.

  * `targetType` : one of the following constants:

      * `aibone`
      * `dice`

This method is equivalent to `askAction("release_object", Dict(TargetType=>targetType, Enqueue=>enqueue))`
