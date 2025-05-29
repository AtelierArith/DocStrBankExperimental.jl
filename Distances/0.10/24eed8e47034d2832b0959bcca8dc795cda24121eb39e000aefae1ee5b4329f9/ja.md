```
Mahalanobis(Q; skipchecks=false) <: Metric
```

共分散行列 `Q` を持つマハラノビス距離（すなわち、双線形形式）を作成します。構築時に、対称性/自己随伴性と正半定性の両方がチェックされますが、後者のチェックはキーワード引数 `skipchecks = true` を渡すことでスキップできます。

# 例:

```julia julia> A = collect(reshape(1:9, 3, 3)); Q = A'A;

julia> dist = Mahalanobis(Q) Mahalanobis{Matrix{Int64}}([14 32 50; 32 77 122; 50 122 194])

julia> dist = Mahalanobis(A, skipchecks=true) ┌ Warning: matrix is not symmetric/Hermitian └ @ Distances ... Mahalanobis{Matrix{Int64}}([1 4 7; 2 5 8; 3 6 9])
```
