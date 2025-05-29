```
Tiling(N::Int[, x::OffsetMatrix{AztecDiamonds.Edge}]; sizehint::Int = N)
```

Represents an order N diamond-shaped tiling. If `x` is not provided, it is initialized with `NONE` representing an empty tiling. The `sizehint` keyword argument may be used to preallocate a larger matrix for `x` fitting a tiling of order `sizehint` to avoid reallocations when the tiling grows.

The indices of `x` represent the coordinates of the diamond-shaped tiling and run from 1-N to N (though `x` is allowed to be larger as long as it contains these indices). The edges it contains can either be `UP`, `RIGHT`, or `NONE`, where `UP` represents a vertical tile covering one more tile to the top, `RIGHT` represents a horizontal tile covering one more tile to the right. `NONE` means the edge is either already covered by another tile to the bottom or left or the tiling is not fully filled yet.

```jldoctest
julia> t = Tiling(1)
Order-1 Tiling{Matrix{AztecDiamonds.Edge}}



julia> t[0, 0] = t[1, 0] = AztecDiamonds.RIGHT;

julia> t
Order-1 Tiling{Matrix{AztecDiamonds.Edge}}
🬇🬋🬋🬃
🬇🬋🬋🬃
```

See [`diamond`](@ref) and [`ka_diamond`](@ref) for constructing a filled tiling.
