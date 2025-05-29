```
ring2nest(m_ring::HealpixMap{T, RingOrder, AA}) where {T, AA}
```

Convert a map from ring to nested order. This version allocates a new array of the same array type as the input.

# Arguments:

  * `m_ring::HealpixMap{T, RingOrder, AA}`: map of type `RingOrder`

# Returns:

  * `HealpixMap{T, NestedOrder, AA}`: the input map converted to `NestedOrder`

# Examples

```julia-repl
julia> m_ring = HealpixMap{Float64,RingOrder}(rand(nside2npix(64)));

julia> ring2nest(m_ring)
49152-element HealpixMap{Float64, NestedOrder, Vector{Float64}}:
 0.0673134062168923
 ⋮
 0.703460503535335
```
