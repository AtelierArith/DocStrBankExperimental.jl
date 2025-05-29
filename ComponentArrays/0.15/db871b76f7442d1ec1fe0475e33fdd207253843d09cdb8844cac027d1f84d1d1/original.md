```
x = ComponentArray(nt::NamedTuple)
x = ComponentArray(;kwargs...)
x = ComponentArray(data::AbstractVector, ax)
x = ComponentArray{T}(args...; kwargs...) where T
```

Array type that can be accessed like an arbitrary nested mutable struct.

# Examples

```jldoctest
julia> using ComponentArrays

julia> x = ComponentArray(a=1, b=[2, 1, 4], c=(a=2, b=[1, 2]))
ComponentVector{Int64}(a = 1, b = [2, 1, 4], c = (a = 2, b = [1, 2]))

julia> x.c.a = 400; x
ComponentVector{Int64}(a = 1, b = [2, 1, 4], c = (a = 400, b = [1, 2]))

julia> x[5]
400

julia> collect(x)
7-element Vector{Int64}:
   1
   2
   1
   4
 400
   1
   2
```
