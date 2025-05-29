```
ax = Axis(nt::NamedTuple)
```

`ComponentArray`のための名前付きコンポーネントアクセスを提供します。

# 例

```jldoctest
julia> using ComponentArrays

julia> ax = Axis((a = 1, b = ViewAxis(2:7, PartitionedAxis(2, (a = 1, b = 2))), c = ViewAxis(8:10, (a = 1, b = 2:3))));

julia> A = [100, 4, 1.3, 1, 1, 4.4, 0.4, 2, 1, 45];

julia> ca = ComponentArray(A, ax)
ComponentVector{Float64}(a = 100.0, b = ComponentVector{Float64, SubArray{Float64, 1, Vector{Float64}, Tuple{UnitRange{Int64}}, true}, Tuple{Axis{(a = 1, b = 2)}}}[(a = 4.0, b = 1.3), (a = 1.0, b = 1.0), (a = 4.4, b = 0.4)], c = (a = 2.0, b = [1.0, 45.0]))

julia> ca.a
100.0

julia> ca.b
3-element LazyArray{ComponentVector{Float64, SubArray{Float64, 1, Vector{Float64}, Tuple{UnitRange{Int64}}, true}, Tuple{Axis{(a = 1, b = 2)}}}}:
 ComponentVector{Float64,SubArray...}(a = 4.0, b = 1.3)
 ComponentVector{Float64,SubArray...}(a = 1.0, b = 1.0)
 ComponentVector{Float64,SubArray...}(a = 4.4, b = 0.4)

julia> ca.c
ComponentVector{Float64,SubArray...}(a = 2.0, b = [1.0, 45.0])

julia> ca.c.b
2-element view(::Vector{Float64}, 9:10) with eltype Float64:
  1.0
 45.0
```
