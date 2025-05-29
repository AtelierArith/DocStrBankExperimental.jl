```
genSpatialPoint(point::Union{NTuple{D, Union{T, Array{T, 0}, ParamBox{T}}}, 
                             AbstractVector}, 
                marker::Symbol=:point) where {D, T<:AbstractFloat} -> 
SpatialPoint{T, D}
```

コレクションの座標コンポーネントから[`SpatialPoint`](@ref)を構築します。 ≡≡≡ 例 ≡≡≡

```jldoctest; setup = :(push!(LOAD_PATH, "../../src/"); using Quiqbox)
julia> v1 = [1.0, 2.0, 3.0];

julia> p1 = genSpatialPoint(v1, :p1)
SpatialPoint{Float64, …}{0, 0, 0}[∂∂∂][(1.0, 2.0, 3.0)]

julia> p1.marker
:p1

julia> v2 = [fill(1.0), 2.0, 3.0];

julia> p2 = genSpatialPoint(v2); p2[1]
ParamBox{Float64, :X, …}{0}[∂][X]⟦=⟧[1.0]

julia> v2[1][] = 1.2
1.2

julia> p2[1]
ParamBox{Float64, :X, …}{0}[∂][X]⟦=⟧[1.2]
```
