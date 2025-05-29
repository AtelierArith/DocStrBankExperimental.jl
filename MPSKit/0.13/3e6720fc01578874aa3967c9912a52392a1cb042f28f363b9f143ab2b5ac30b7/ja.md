```julia
struct VOMPS{F} <: MPSKit.Algorithm
```

無限MPOの支配的固有ベクトルを見つけるための冪法アルゴリズム。この方法は、演算子と状態の積を同じボンド次元の新しい状態で反復的に近似することによって機能します。

## フィールド

  * `tol::Float64`: 収束基準のための許容誤差
  * `maxiter::Int64`: 最大反復回数
  * `verbosity::Int64`: 表示される情報の量を設定する
  * `alg_gauge::Any`: `InfiniteMPS`のゲージに使用されるアルゴリズム
  * `alg_environments::Any`: MPS環境に使用されるアルゴリズム
  * `finalize::Any`: 各反復後に適用されるコールバック関数、シグネチャは`finalize(iter, ψ, H, envs) -> ψ, envs`

## 参考文献

  * [Vanhecke et al. SciPost Phys. Core 4 (2021)](@cite vanhecke2021)
