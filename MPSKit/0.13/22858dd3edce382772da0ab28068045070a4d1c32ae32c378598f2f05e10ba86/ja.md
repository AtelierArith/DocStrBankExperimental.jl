```julia
struct IDMRG2{A, S} <: MPSKit.Algorithm
```

二サイト無限DMRGアルゴリズムは、支配的な固有ベクトルを見つけるためのものです。

## フィールド

  * `tol::Float64`: 収束基準のための許容誤差
  * `maxiter::Int64`: 最大反復回数
  * `verbosity::Int64`: 表示される情報の量を設定するためのもの
  * `alg_gauge::Any`: MPSのゲージに使用されるアルゴリズム
  * `alg_eigsolve::Any`: 固有値ソルバーに使用されるアルゴリズム
  * `alg_svd::Any`: 特異値分解に使用されるアルゴリズム
  * `trscheme::TensorKit.TruncationScheme`: 二サイト更新のための[切り捨て](@extref TensorKit.tsvd)に使用されるアルゴリズム
