```
PHDFilter(γ::GaussianMixture, spawn::Spawn, dyn::Vector{Dynamics},
    meas::Measurement, Ps::Float64, Pd::Float64, κ::Function)
PHDFilter(γ::GaussianMixture, spawn::Spawn, dyn::Dynamics,
    meas::Measurement, Ps::Float64, Pd::Float64, κ::Function)

PHDフィルタを設定します

引数:
γ: 出生強度
spawn: スポーン強度
dyn: 可能なダイナミクスモデルのベクトル
meas: 測定値
Ps: 生存確率
Pd: 検出確率
```
