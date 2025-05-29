```julia
struct DMRG{A, F} <: MPSKit.Algorithm
```

単一サイトDMRGアルゴリズムは、支配的な固有ベクトルを見つけるためのものです。

## フィールド

  * `tol::Float64`: 収束基準のための許容誤差
  * `maxiter::Int64`: 最大反復回数
  * `verbosity::Int64`: 表示される情報の量を設定する
  * `alg_eigsolve::Any`: 固有値ソルバーに使用されるアルゴリズム
  * `finalize::Any`: 各反復後に適用されるコールバック関数、シグネチャは `finalize(iter, ψ, H, envs) -> ψ, envs`
