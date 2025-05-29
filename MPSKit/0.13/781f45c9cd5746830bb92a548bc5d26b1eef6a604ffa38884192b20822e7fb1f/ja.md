```julia
struct OptimalExpand{S} <: MPSKit.Algorithm
```

与えられた mps を [Zauner-Stauber et al. Phys. Rev. B 97 (2018)](@cite zauner-stauber2018) に記載された通りに拡張するアルゴリズムで、元の ψ に直交する二サイト更新 MPS テンソルの支配的な寄与を選択します。

## フィールド

  * `alg_svd::Any`: 特異値分解に使用されるアルゴリズム
  * `trscheme::TensorKit.TruncationScheme`: 拡張された空間を切り捨てるために使用されるアルゴリズム
