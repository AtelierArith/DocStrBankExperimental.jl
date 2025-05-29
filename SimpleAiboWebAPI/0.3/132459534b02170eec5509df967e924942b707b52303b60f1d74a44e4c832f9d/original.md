```
askMoveToPosition(
  targetType="charging_station";
  enqueue=false,
  target_deviceID=nothing,
  target_nickname=nothing,
  timeoutLimit=10)
```

asks `move_to_position`.

  * `targetType` : one of the following constants:

      * `charging_station`
      * `greeting_spot`
      * `toilet`

This method is equivalent to `askAction("move_to_position", Dict(TargetType=>targetType, Enqueue=>enqueue))`
