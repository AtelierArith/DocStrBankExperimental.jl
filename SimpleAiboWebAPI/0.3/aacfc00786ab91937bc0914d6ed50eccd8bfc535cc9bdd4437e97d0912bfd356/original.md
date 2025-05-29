```
askApproachPerson(
  distanceFromTarget=1;
  enqueue=false,
  target_deviceID=nothing,
  target_nickname=nothing,
  timeoutLimit=10)
```

asks `approach_person`.

  * `distanceFromTarget` : 0.4 – 2 (meter)

This method is equivalent to `askAction("approach_person", Dict(DistanceFromTarget=>distanceFromTarget, Enqueue=>enqueue))`
