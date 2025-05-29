```julia
struct DynamicalDMRG{F<:MPSKit.DDMRG_Flavour, S} <: MPSKit.Algorithm
```

動的相互作用密度行列理論（DMRG）法を用いて、動的特性と励起状態を計算するための方法であり、動的相関関数に対する変分原理に基づいています。

## フィールド

  * `flavour::MPSKit.DDMRG_Flavour`: 使用するアルゴリズムのフレーバーで、[`NaiveInvert`](@ref) または [`Jeckelmann`](@ref) のいずれかの型
  * `solver::Any`: 線形ソルバーに使用されるアルゴリズム
  * `tol::Float64`: 収束基準の許容誤差
  * `maxiter::Int64`: 最大反復回数
  * `verbosity::Int64`: 表示される情報の量に関する設定

## 参考文献

  * [Jeckelmann. Phys. Rev. B 66 (2002)](@cite jeckelmann2002)
