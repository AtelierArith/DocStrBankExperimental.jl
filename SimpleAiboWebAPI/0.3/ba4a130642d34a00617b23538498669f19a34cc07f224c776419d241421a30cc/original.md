```
askGetCloseToObject(
  targetType="pinkball";
  distance=0.2,
  enqueue=false,
  target_deviceID=nothing,
  target_nickname=nothing,
  timeoutLimit=10)
```

asks `get_close_to_object`. Invoke this method after `askApproachObject`.

  * `targetType` : one of the following constants:

      * `aibo`
      * `aibone`
      * `dice`
      * `pinkball`
  * `distance` : 0.1 – 0.3 (meter)

This method is equivalent to `askAction("get_close_to_object", Dict(TargetType=>targetType, Distance=>distance, Enqueue=>enqueue))`
