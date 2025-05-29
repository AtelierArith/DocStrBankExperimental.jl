```julia
struct IDMRG{A} <: MPSKit.Algorithm
```

単一サイト無限DMRGアルゴリズムによる支配的固有ベクトルの発見。

## フィールド

  * `tol::Float64`: 収束基準の許容誤差
  * `maxiter::Int64`: 最大反復回数
  * `verbosity::Int64`: 表示される情報の量を設定する
  * `alg_gauge::Any`: MPSのゲージに使用されるアルゴリズム
  * `alg_eigsolve::Any`: 固有値ソルバーに使用されるアルゴリズム
