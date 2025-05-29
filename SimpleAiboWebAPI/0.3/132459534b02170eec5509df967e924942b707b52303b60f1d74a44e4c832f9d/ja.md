```
askMoveToPosition(
  targetType="charging_station";
  enqueue=false,
  target_deviceID=nothing,
  target_nickname=nothing,
  timeoutLimit=10)
```

は `move_to_position` を要求します。

  * `targetType` : 次の定数のいずれか：

      * `charging_station`
      * `greeting_spot`
      * `toilet`

このメソッドは `askAction("move_to_position", Dict(TargetType=>targetType, Enqueue=>enqueue))` と同等です。
