```
evaluate_function(
    f::Vector{Float64},
    region::Set{Int64};
    qdim::Int64 = 1
) -> Vector{Float64}
```

与えられた領域内のすべてのノードでFEM係数ベクトルとして与えられた離散関数を評価します。結果のベクトルは、フル係数ベクトルの長さを持ち、評価されていないノードに対応するエントリはゼロになります。
