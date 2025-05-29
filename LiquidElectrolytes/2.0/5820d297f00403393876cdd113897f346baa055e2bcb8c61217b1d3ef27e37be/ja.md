```julia
struct SawTooth
```

サンプル関数を定義する呼び出し可能な（ファンクタ）構造体。

`(::SawTooth)(t)` は、時刻 t に適用される電圧を返します。

  * `vmin::Float64`: 最小電圧。デフォルト: -1V。
  * `vmax::Float64`: 最大電圧。デフォルト: 1V。
  * `scanrate::Float64`: スキャンレート。デフォルト: 0.1V/s。
  * `vstart::Float64`: 開始電圧。デフォルト: 0V
  * `tstart::Float64`: 開始時間。デフォルト: 0s
  * `scanup::Bool`: 初期スキャン方向。デフォルト: true
