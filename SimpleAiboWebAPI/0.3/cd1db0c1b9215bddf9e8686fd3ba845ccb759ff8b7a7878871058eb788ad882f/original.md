```
askTurnAround(;
  turnAngle=0,
  turnSpeed=1,
  enqueue=false,
  target_deviceID=nothing,
  target_nickname=nothing,
  timeoutLimit=10)
```

asks `turn_around`.

  * `turnSpeed` : one of 0 (slow), 1, 2 (fast)
  * `turnAngle` : -180 – 180, counterclockwise with respect to the current aibo angle.

This method is equivalent to `askAction("turn_around", Dict(TurnSpeed=> turnSpeed, TurnAngle=> turnAngle, Enqueue=>enqueue))`
