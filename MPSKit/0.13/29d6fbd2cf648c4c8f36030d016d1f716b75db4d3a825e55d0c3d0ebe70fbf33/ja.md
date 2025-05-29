```julia
struct RandExpand{S} <: MPSKit.Algorithm
```

既存の状態に直交するランダムユニタリベクトルを追加することでボンド次元を拡張するアルゴリズムです。これは、既存の状態に直交するように作られたランダムな二サイトMPSテンソルに対して切り捨てSVDを実行することで達成されます。

## フィールド

  * `alg_svd::Any`: 特異値分解に使用されるアルゴリズム
  * `trscheme::TensorKit.TruncationScheme`: 拡張された空間の[切り捨て](@extref TensorKit.tsvd)に使用されるアルゴリズム
