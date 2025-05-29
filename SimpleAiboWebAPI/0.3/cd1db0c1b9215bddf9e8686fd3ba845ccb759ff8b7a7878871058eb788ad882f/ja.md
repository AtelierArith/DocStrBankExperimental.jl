```
askTurnAround(;
  turnAngle=0,
  turnSpeed=1,
  enqueue=false,
  target_deviceID=nothing,
  target_nickname=nothing,
  timeoutLimit=10)
```

`turn_around`を要求します。

  * `turnSpeed` : 0（遅い）、1、2（速い）のいずれか
  * `turnAngle` : -180 – 180、現在のaiboの角度に対して反時計回り。

このメソッドは、`askAction("turn_around", Dict(TurnSpeed=> turnSpeed, TurnAngle=> turnAngle, Enqueue=>enqueue))`と同等です。
