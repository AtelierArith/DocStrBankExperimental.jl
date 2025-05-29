```
tiles(s::AbstractScheme, A)
tiles(s::AbstractExtendScheme, A)
```

Construct 1 or more `Tiles` by partitioning `A` according to the index (`s.g` if `AbstractScheme`, `s.h` if `AbstractExtendScheme`), then calling `tile(s, B)` on each partition `B`. Returns a vector of tiles, each of which bears the index that defined the partition.

See also: [`tile`](@ref)

# Examples

```jldoctest
julia> A = reshape(-12:12, 5, 5); B = eachcol(A);

julia> s = @scheme sum signbit ∘ (x -> x[begin+2]);

julia> tiles(s, B)
2-element Vector{Tile{Vector{Int64}, Int64, Tuple{Bool}, Bool, 1}}:
 [-50, -25]
 [0, 25, 50]
```
