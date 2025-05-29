```
SweptSine(F, tstart, duration, fstart, fend, type)
```

スイープサイン励振信号を定義する構造体

**フィールド**

  * `F::Real`: 力の振幅 [N]
  * `tstart::Real`: 励振の開始時間 [s]
  * `duration::Real`: 励振の持続時間 [s]
  * `fstart::Real`: 開始周波数 [Hz]
  * `fend::Real`: 終了周波数 [Hz]
  * `type::Symbol`: スイープのタイプ

      * `:lin` - 線形（デフォルト）
      * `:quad` - 二次
      * `:log` - 対数
  * `zero_end::Bool`: 持続時間の終了時に励振を0に設定するためのブール値（デフォルト = true）
