```
evaluate_function(
    f::Vector{Float64},
    node::Int64;
    qdim::Int64 = 1
) -> Vector{Float64}
```

与えられたノードでFEM係数ベクトルとして与えられた離散関数を評価します。結果のベクトルはfの成分の数の長さを持ちます。
