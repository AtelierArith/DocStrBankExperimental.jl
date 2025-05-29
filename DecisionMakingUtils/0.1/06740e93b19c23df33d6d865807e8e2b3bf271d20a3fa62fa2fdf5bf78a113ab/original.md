```
TileCodingBasis(num_inputs::Int, num_tiles::Int; num_tilings::Int, tiling_type::Symbol=:wrap, tile_loc::Symbol=:equal)
```

Creates a tile coding basis with `num_inputs` inputs and `num_tiles` tiles per input.  `num_tilings` represents the number of different tilings to use.  `tiling_type` can be either `:wrap` or `:clip`, and determines whether the tiles wrap around the edges of the input space or are clipped to the edges. `tile_loc` can be either `:equal` or `:random`, and determines whether the tiles are spread equally across the input space or are randomly distributed. Alternatively, construction can just specify `num_tiles` as a vector of integers, specifying the number of tiles per input. The tiles are spread equally across [0,1] for each input. The basis is implemented as a sparse vector, where each element is 1 if the input is in the corresponding tile, and 0 otherwise.

See also: [`FourierBasisBuffer`](@ref)

# Examples

```jldoctest
julia> f = TileCodingBasis(2, 3, num_tilings=1, tiling_type=:wrap, tile_loc=:equal);

julia> x = [0.0, 0.0];

julia> feats = f(x)
(1,)

julia> feats = f([1,1])  # at 1.0 the inputs wrap around to 0.0
(1,)

julia> feats = f([0.99,0.99]) 
(9,)

julia> length(f)
9

julia> size(f)
(9,1)

julia> f = TileCodingBasis([10,10,3], num_tilings=2);

julia> length(f)
600

julia> size(f)
(300,2)

julia> f([0.0, 0.0, 0.99])  # this is in the last 100 tiles for the first tiling
(201,1)

```
