```julia
struct VUMPSSvdCut <: MPSKit.Algorithm
```

状態のボンド次元を変更するために二サイト更新ステップを使用するアルゴリズムです。

## フィールド

  * `alg_gauge::Any`: `InfiniteMPS`のゲージに使用されるアルゴリズム
  * `alg_eigsolve::Any`: 固有値ソルバーに使用されるアルゴリズム
  * `alg_svd::Any`: 特異値分解に使用されるアルゴリズム
  * `trscheme::TensorKit.TruncationScheme`: 二サイト更新の[切り捨て][@extref TensorKit.tsvd]に使用されるアルゴリズム
