```
askMoveDirection(;
  targetAngle=0,
  targetDistance=1,
  walkSpeed=1,
  enqueue=false,
  target_deviceID=nothing,
  target_nickname=nothing,
  timeoutLimit=10)
```

`move_direction`を要求します。

  * `walkSpeed`      : 0（遅い）、1、2（速い）のいずれか
  * `targetDistance` : 0 – 6（メートル）
  * `targetAngle`    : -180 – 180、現在のaiboの角度に対して反時計回り。

このメソッドは、`askAction("move_direction", Dict(WalkSpeed=> walkSpeed, TargetDistance=> targetDistance, TargetAngle=> targetAngle, Enqueue=>enqueue))`と同等です。
