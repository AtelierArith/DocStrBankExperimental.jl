```
askMoveAlongCircle(;
  movingAngle=360,
  radius=1,
  walkSpeed=1,
  enqueue=false,
  target_deviceID=nothing,
  target_nickname=nothing,
  timeoutLimit=10)
```

asks `move_along_circle`.

  * `walkSpeed`   : one of 0 (slow), 1, 2 (fast)
  * `radius`      : 0.5 – 3 (meter)
  * `movingAngle` : 0 – 1080 (degree)

This method is equivalent to `askAction("move_along_circle", Dict(WalkSpeed=> walkSpeed, Radius=> radius, MovingAngle=>movingAngle, Enqueue=>enqueue))`
