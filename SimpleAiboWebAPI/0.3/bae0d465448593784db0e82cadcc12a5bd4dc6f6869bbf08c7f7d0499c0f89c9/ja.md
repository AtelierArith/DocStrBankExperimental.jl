```
askChasePerson(
  chasingDurationMsec=15*1000;
  enqueue=false,
  target_deviceID=nothing,
  target_nickname=nothing,
  timeoutLimit=10)
```

`chase_person`に尋ねます。

  * `chasingDurationMsec` : 0 – 360000 (ミリ秒)

このメソッドは、`askAction("chase_person", Dict(ChasingDurationMsec=>chasingDurationMsec, Enqueue=>enqueue))`と同等です。
