```
confusion([T = Int],
          a::Union{ClusteringResult, AbstractVector},
          b::Union{ClusteringResult, AbstractVector}) -> Matrix{T}
```

2つのクラスタリングの*混同行列*を計算します。

2つのクラスタリング`a`と`b`の間のパーティションの共起または類似性行列を表す、型`T`（デフォルトは`Int`）の2×2混同行列`C`を返します。すべてのサンプルのペアを考慮し、同じクラスタに割り当てられたペアや異なるクラスタに割り当てられたペアをカウントします。

同じグループにいるサンプルのペアを**正のペア**、異なるグループにいるペアを**負のペア**とすると、真の陽性のカウントは`C₁₁`、偽陰性は`C₁₂`、偽陽性は`C₂₁`、真の陰性は`C₂₂`です：

|          | Positive | Negative |
|:--------:|:--------:|:--------:|
| Positive |   C₁₁    |   C₁₂    |
| Negative |   C₂₁    |   C₂₂    |

## 参照

完全な*コンティンジェンシー行列*については[`counts(a::ClusteringResult, a::ClusteringResult)`](@ref counts)を参照してください。
