```
jacobian(
    terms::AbstractVector{<:Node},
    partial_variables::AbstractVector{<:Node}
)
```

`terms`によって定義されたn要素関数のヤコビ行列。各項要素はNode式グラフです。ヤコビ行列の列は`partial_variables`の要素に対応するもののみが計算され、ヤコビ行列の部分列は`partial_variables`で指定された順序になります。例:

```julia
julia> @variables x y

julia> jacobian([x*y,y*x],[x,y])
2×2 Matrix{Node}:
 y  x
 y  x

julia> jacobian([x*y,y*x],[y,x])
2×2 Matrix{Node}:
 x  y
 x  y

julia> jacobian([x*y,y*x],[x])
2×1 Matrix{Node}:
 y
 y
```
