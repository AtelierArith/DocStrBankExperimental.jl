```
qnorm_boundary(
    p::Float64,
    v::AbstractVector{Float64},
    mesh::Mesh;
    boundaryElements::Set{Int64} = Set{Int64}(),
    qdim::Int64 = 1,
    order::Int64 = 1
) -> Float64
```

境界要素上の与えられたメッシュにおけるノードまたは数値積分点での関数 f またはその FEM 係数ベクトル v の $L^q$-ノルムを返します。ここで、q は p に対する共役指数です。
