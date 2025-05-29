```
UndefArray(size [, factory])
UndefArray{T}(size [, factory])
UndefArray{T,N}(size [, factory])
```

# Examples

```jldoctest
julia> using MicroCollections

julia> UndefArray((2,))
2-element UndefVector{Union{}}(2):
 #undef
 #undef

julia> UndefArray{Int}((2, 3))
2×3 UndefArray{2,Int64}((2, 3)):
 #undef  #undef  #undef
 #undef  #undef  #undef
```

The size of an `UndefArray` can be "changed" by using [`Accessors.@set`](https://github.com/JuliaObjects/Accessors.jl)

```jldoctest; setup = :(using MicroCollections, Accessors)
julia> using Accessors

julia> x = UndefArray((2,))
2-element UndefVector{Union{}}(2):
 #undef
 #undef

julia> @set size(x) = (1, 3)
1×3 UndefArray{2,Union{}}((1, 3)):
 #undef  #undef  #undef
```
