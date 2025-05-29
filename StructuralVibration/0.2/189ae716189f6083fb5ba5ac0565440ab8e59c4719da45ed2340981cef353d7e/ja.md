```
SineWave(F, tstart, duration, freq; zero_end = true)
```

サイン波励起信号を定義する構造体

**コンストラクタパラメータ**

  * `F::Real`: 力の振幅 [N]
  * `tstart::Real`: 励起の開始時間 [s]
  * `duration::Real`: 励起の持続時間 [s]
  * `freq::Real`: 励起の周波数 [Hz]
  * `zero_end::Bool`: 持続時間の終わりで励起を0に設定するためのブール値（デフォルト = true）

**フィールド**

  * `F::Real`: 力の振幅 [N]
  * `tstart::Real`: 励起の開始時間 [s]
  * `duration::Real`: 励起の持続時間 [s]
  * `ω::Real`: 励起の周波数 [Hz]
  * `zero_end::Bool`: 持続時間の終わりで励起を0に設定するためのブール値（デフォルト = true）
