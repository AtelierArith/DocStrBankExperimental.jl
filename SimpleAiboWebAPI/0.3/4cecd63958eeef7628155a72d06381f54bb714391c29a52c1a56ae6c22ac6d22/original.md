```
askApproachObject(
  targetType="pinkball";
  enqueue=false,
  target_deviceID=nothing,
  target_nickname=nothing,
  timeoutLimit=10)
```

asks `approach_object`.

  * `targetType` : one of the following constants:

      * `aibo`
      * `aibone`
      * `dice`
      * `pinkball`

This method is equivalent to `askAction("approach_object", Dict(TargetType=>targetType, Enqueue=>enqueue))`
