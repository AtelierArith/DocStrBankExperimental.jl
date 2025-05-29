```julia
struct Generator
```

静的発電機属性のための型（すなわち、時系列データではない発電機を説明するもの）。`pu`で与えられるパラメータは、基準電力が100MWであることを前提としています。

フィールド：

  * `unit_code::Int64`: 発電機のID/ユニットコード
  * `zone::Int64`: 発電機が所在するゾーンの番号
  * `startup_cost::Float64`: 発電機を起動するコスト（$）
  * `shutdown_cost::Float64`: 発電機を停止するコスト（$）
  * `no_load_cost::Float64`: 発電機が稼働しているがMWを生産していない場合のコスト（:/時間）
  * `min_uptime::Float64`: 発電機が稼働しなければならない最小時間（時間）
  * `min_downtime::Float64`: 発電機が停止していなければならない最小時間（時間）
  * `ramp_up::Float64`: 発電機が発電を増加させることができる速度（pu/分）
  * `ramp_down::Float64`: 発電機が発電を減少させることができる速度（pu/分）
  * `technology::Symbol`: 発電機の技術を説明するシンボル
