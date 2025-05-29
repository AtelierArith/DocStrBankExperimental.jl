```
pnorm_boundary(
    p::Float64,
    v::AbstractVector{Float64},
    mesh::Mesh;
    boundaryElements::Set{Int64} = Set{Int64}(),
    qdim::Int64 = 1,
    order::Int64 = 1
) -> Float64
```

与えられたメッシュ上の境界要素におけるノードまたは数値積分点でのFEM係数ベクトルvの$L^p$-ノルムを返します。p=Infの場合、値は補間または外挿されず、したがって領域全体の真の最大値ではなく、与えられたデータの最大値のみである可能性があります。
