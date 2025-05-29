```julia
struct SvdCut{S} <: MPSKit.Algorithm
```

トランケートSVDを使用してψのボンド次元を変更するアルゴリズムです。

## フィールド

  * `alg_svd::Any`: 特異値分解に使用されるアルゴリズム
  * `trscheme::TensorKit.TruncationScheme`: ゲージテンソルの[切り捨て][@extref TensorKit.tsvd]に使用されるアルゴリズム
