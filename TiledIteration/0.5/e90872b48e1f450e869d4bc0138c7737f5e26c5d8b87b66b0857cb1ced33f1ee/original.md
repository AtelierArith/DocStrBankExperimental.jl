```
SplitAxes(axs::NTuple{N,AbstractUnitRange}, n::Real)
```

Split `axs` into `ceil(Int, n)` approximately equal-sized chunks along the final dimension represented by `axs`.

See [`SplitAxis`](@ref) for further details.

# Examples

```jldoctest; setup=:(using TiledIteration)
julia> A = rand(3, 16);

julia> collect(SplitAxes(axes(A), 4))
4-element Vector{Tuple{UnitRange{Int64}, UnitRange{Int64}}}:
 (1:3, 1:4)
 (1:3, 5:8)
 (1:3, 9:12)
 (1:3, 13:16)
```
