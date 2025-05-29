```
getMotionFreq(bSF::MPIFile, bMeas::MPIFile, choosePeak::Int)
```

各パッチおよびフレームの信号変調の周波数 [Hz] を決定します

...

  * `bSF::MPIFile`: システム関数 ==> モーション周波数は高いSNRを持つ成分からのみ決定されるため、必須です
  * `bMeas::MPIFile`: 測定
  * `choosePeak::Int`: 測定信号内で異なる変調や高調波を見つけることができます。

選択したいピークの番号を選んでください ...
