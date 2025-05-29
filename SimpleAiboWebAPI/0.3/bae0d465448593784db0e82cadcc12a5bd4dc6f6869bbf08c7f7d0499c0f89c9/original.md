```
askChasePerson(
  chasingDurationMsec=15*1000;
  enqueue=false,
  target_deviceID=nothing,
  target_nickname=nothing,
  timeoutLimit=10)
```

asks `chase_person`.

  * `chasingDurationMsec` : 0 – 360000 (milliseconds)

This method is equivalent to `askAction("chase_person", Dict(ChasingDurationMsec=>chasingDurationMsec, Enqueue=>enqueue))`
