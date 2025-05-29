```
Parallelepiped(vecs)
Parallelepiped(vecs::T) where {T<:Real}
```

単一の値または行列の列ベクトルを使用して、`vecs`の次元に応じて線分、平行四辺形、または平行六面体の領域を定義します。これは[`BoundedLattice`](@ref)を作成するために使用できます。

```jldoctest; setup=:(using BloqadeLattices)
julia> Parallelepiped(2.0) # 1D格子を制約できます
Parallelepiped{1, Float64}([2.0;;], [0.5;;])

julia> bounds = zeros((2,2)); # 2D領域を定義するベクトルを格納する2x2行列を作成

julia> bounds[:,1] .= (3,3); bounds[:,2] .= (4,0); # 列ベクトルが平行四辺形を定義

julia> Parallelepiped(bounds)
Parallelepiped{2, Float64}([3.0 4.0; 3.0 0.0], [0.0 0.3333333333333333; 0.25 -0.25])
```
