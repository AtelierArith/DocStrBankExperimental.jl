```
TileCodingModel([::Type,] ϕ; num_tiles, num_tilings, num_outputs=1, num_actions=1)
```

Creates a linear function that assumes ϕ is a tile coding basis function, returns an int or tuple/list of ints representing the tile for each tiling.  This struct supports multiple outputs (num*outputs > 1) and action conditioned prediction (num*actions > 1).  A TabularModel is also a special case of the tile coding model that uses an identity basis function, with one tiling, and number of tiles equal to the number of states. 

See also: [`TabularModel`](@ref), [`LinearModel`](@ref)

# Examples

```jldoctest
julia> ϕ = TileCodingBasis(1, 3, num_tilings=1, tiling_type=:clip, tile_loc=:equal);

julia> num_tiles, num_tilings = size(ϕ);

julia> m = TileCodingModel(ϕ, num_tiles=num_tiles, num_tilings=num_tilings);

julia> vec(params(m)) .= 1:length(params(m));

julia> [m(i) for i in [0.0, 0.5, 1.0]]
3-element Vector{Float64}:
 1.0
 2.0
 3.0

julia> v, g = value_withgrad(m, 0.5);

julia> v
2.0

julia> g  # only the active tile has a non zero gradient
1×3×1×1 Array{Float64, 4}:
[:, :, 1, 1] =
 0.0  1.0  0.0

```
