```
recombination_matrix(R::AbstractBSplineBasis)
```

再結合された基底に関連する [`RecombineMatrix`](@ref) を取得します。

[`BSplineBasis`](@ref) のような再結合されていない基底の場合、これは単位行列 (`LinearAlgebra.I`) を返します。
