```
askFindObject(
  targetType="pinkball";
  enqueue=false,
  target_deviceID=nothing,
  target_nickname=nothing,
  timeoutLimit=10)
```

asks `find_object`.

  * `targetType` : one of the following constants:

      * `aibo`
      * `aibone`
      * `dice`
      * `pinkball`

This method is equivalent to `askAction("find_object", Dict(TargetType=>targetType, Enqueue=>enqueue))`
