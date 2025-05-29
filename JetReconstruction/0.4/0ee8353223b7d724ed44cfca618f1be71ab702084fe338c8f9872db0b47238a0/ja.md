```
mutable struct EEjet
```

`EEjet`構造体は、e+eジェット再構成ルーチンに使用される4-運動量オブジェクトです。

# フィールド

  * `px::Float64`: ジェット運動量のx成分。
  * `py::Float64`: ジェット運動量のy成分。
  * `pz::Float64`: ジェット運動量のz成分。
  * `E::Float64`: ジェットのエネルギー。
  * `_cluster_hist_index::Int`: クラスターヒストグラムのインデックス。
  * `_p2::Float64`: ジェットの二乗運動量。
  * `_inv_p::Float64`: ジェットの逆運動量。
