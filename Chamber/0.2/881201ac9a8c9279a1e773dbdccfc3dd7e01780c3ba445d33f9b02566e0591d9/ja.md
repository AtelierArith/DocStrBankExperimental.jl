```
heat_conduction_chamber_profileCH(maxn::Int64, a::Float64, c::Float64, r::Float64, kappa::Float64, Tb::Float64, param_sv::ParamSaved{Float64})::Float64
```

マグマチャンバー内の熱伝達を、母岩の熱拡散率と外殻の温度プロファイルに基づいて計算します。

## 引数

  * `maxn`: 項の数
  * `a`: マグマチャンバーの半径 (m)
  * `c`: 外殻の半径 (m)
  * `r`: 熱伝達を計算するためのグリッド間隔
  * `kappa`: 母岩の熱拡散率
  * `Tb`: 外殻の境界温度 (K)
  * `param_sv`: 関数の以前の結果を保存する構造体 `ParamSaved`

## 戻り値

  * `Trt`
