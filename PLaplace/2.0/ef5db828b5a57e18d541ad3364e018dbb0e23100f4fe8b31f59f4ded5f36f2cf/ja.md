```
compute_normalderivative(
    mesh::Mesh,
    boundary::Set{Boundary},
    v::AbstractVector{Float64};
    qdim::Int64 = 1
) -> Dict{Tuple{Int64, Int64}, AbstractVector{Float64}}
```

前の `compute_normalderivative(...)` と同様です。ただし、引数 `boundary` として名前付き境界オブジェクトの `Set{Boundary}` を受け取り、与えられた境界に含まれるノードのインデックスを含む `Set{Int64}` に変換します。
