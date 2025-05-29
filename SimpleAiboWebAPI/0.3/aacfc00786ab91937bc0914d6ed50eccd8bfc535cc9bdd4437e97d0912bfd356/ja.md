```
askApproachPerson(
  distanceFromTarget=1;
  enqueue=false,
  target_deviceID=nothing,
  target_nickname=nothing,
  timeoutLimit=10)
```

`approach_person`に尋ねます。

  * `distanceFromTarget` : 0.4 – 2 (メートル)

このメソッドは、`askAction("approach_person", Dict(DistanceFromTarget=>distanceFromTarget, Enqueue=>enqueue))`と同等です。
