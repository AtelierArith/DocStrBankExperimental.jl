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

asks `move_direction`.

  * `walkSpeed`      : one of 0 (slow), 1, 2 (fast)
  * `targetDistance` : 0 – 6 (meter)
  * `targetAngle`    : -180 – 180, counterclockwise with respect to the current aibo angle.

This method is equivalent to `askAction("move_direction", Dict(WalkSpeed=> walkSpeed, TargetDistance=> targetDistance, TargetAngle=> targetAngle, Enqueue=>enqueue))`
