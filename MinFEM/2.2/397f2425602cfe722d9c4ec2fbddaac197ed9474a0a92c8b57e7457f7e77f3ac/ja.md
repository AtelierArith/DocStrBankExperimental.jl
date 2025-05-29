```
pnorm(
    p::Float64,
    v::AbstractVector{Float64},
    mesh::Mesh; 
    qdim::Int64 = 1,
    order::Int64 = 1
) -> Float64
```

与えられたメッシュ上の要素内のノードまたは数値積分点におけるFEM係数ベクトルvの$L^p$-ノルムを返します。p=Infの場合、値は補間または外挿されず、したがって領域全体の真の最大値ではなく、与えられたデータの最大値のみである可能性があります。
