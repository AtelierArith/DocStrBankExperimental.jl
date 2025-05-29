```
askMoveForward(;
  walkDistance=1,
  walkSpeed=1,
  enqueue=false,
  target_deviceID=nothing,
  target_nickname=nothing,
  timeoutLimit=10)
```

`move_forward`を要求します。

  * `walkSpeed`    : 0（遅い）、1、2（速い）のいずれか
  * `walkDistance` : -6 ～ 6（メートル）

このメソッドは、`askAction("move_forward", Dict(WalkSpeed=> walkSpeed, WalkDistance=> walkDistance, Enqueue=>enqueue))`と同等です。
