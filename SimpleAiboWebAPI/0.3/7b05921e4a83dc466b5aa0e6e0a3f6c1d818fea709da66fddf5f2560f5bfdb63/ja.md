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

`move_along_circle`を要求します。

  * `walkSpeed`   : 0（遅い）、1、2（速い）のいずれか
  * `radius`      : 0.5 – 3（メートル）
  * `movingAngle` : 0 – 1080（度）

このメソッドは、`askAction("move_along_circle", Dict(WalkSpeed=> walkSpeed, Radius=> radius, MovingAngle=>movingAngle, Enqueue=>enqueue))`と同等です。
