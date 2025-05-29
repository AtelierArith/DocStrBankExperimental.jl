```
askChaseObject(
  targetType="pinkball";
  chasingDurationMsec=30*1000,
  enqueue=false,
  target_deviceID=nothing,
  target_nickname=nothing,
  timeoutLimit=10)
```

asks `chase_object`.

  * `targetType` : one of the following constants:

      * `aibo`
      * `aibone`
      * `dice`
      * `pinkball`
  * `chasingDurationMsec` : 0 – 360000 (milliseconds)

This method is equivalent to `askAction("chase_object", Dict(TargetType=>targetType, ChasingDurationMsec=> chasingDurationMsec, Enqueue=>enqueue))`
