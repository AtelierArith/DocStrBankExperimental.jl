```julia
struct SegmentedVector{K, T, KeyRange<:AbstractRange{K}, P<:AbstractArray{T, 1}} <: AbstractArray{T, 1}
```

`SegmentedVector` は、別の `AbstractVector`（その親）によってバックアップされる `AbstractVector` であり、さらに親へのビューを含む [`IndexDict`](@ref) を格納します。これらのビューは、親をカバーします。

# 例

```julia-repl
julia> x = [1., 2., 3., 4.]
4-element Array{Float64,1}:
 1.0
 2.0
 3.0
 4.0

julia> viewlength(i) = 2
viewlength (generic function with 1 method)

julia> xseg = SegmentedVector{Int}(x, 1 : 2, viewlength)
4-element RigidBodyDynamics.CustomCollections.SegmentedVector{Int64,Float64,Base.OneTo{Int64},Array{Float64,1}}:
 1.0
 2.0
 3.0
 4.0

julia> segments(xseg)[1]
2-element SubArray{Float64,1,Array{Float64,1},Tuple{UnitRange{Int64}},true}:
 1.0
 2.0

julia> yseg = similar(xseg, Int32); yseg .= 1 : 4 # 同じビュー範囲、異なる要素タイプ
4-element RigidBodyDynamics.CustomCollections.SegmentedVector{Int64,Int32,Base.OneTo{Int64},Array{Int32,1}}:
 1
 2
 3
 4

julia> segments(yseg)[2]
2-element SubArray{Int32,1,Array{Int32,1},Tuple{UnitRange{Int64}},true}:
 3
 4
```
