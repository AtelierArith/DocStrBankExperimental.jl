```
qnorm(
    p::Float64,
    v::AbstractVector{Float64},
    mesh::Mesh;
    qdim::Int64 = 1,
    order::Int64 = 1
) -> Float64
```

与えられたメッシュ上の要素内のノードまたは数値積分点に対するFEM係数ベクトルvの$L^q$-ノルムを返します。ここで、qはpに対する共役指数です。
