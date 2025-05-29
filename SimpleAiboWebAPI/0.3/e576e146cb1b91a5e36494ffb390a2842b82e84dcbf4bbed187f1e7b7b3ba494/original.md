```
askMoveForward(;
  walkDistance=1,
  walkSpeed=1,
  enqueue=false,
  target_deviceID=nothing,
  target_nickname=nothing,
  timeoutLimit=10)
```

asks `move_forward`.

  * `walkSpeed`    : one of 0 (slow), 1, 2 (fast)
  * `walkDistance` : -6 – 6 (meter)

This method is equivalent to `askAction("move_forward", Dict(WalkSpeed=> walkSpeed, WalkDistance=> walkDistance, Enqueue=>enqueue))`
