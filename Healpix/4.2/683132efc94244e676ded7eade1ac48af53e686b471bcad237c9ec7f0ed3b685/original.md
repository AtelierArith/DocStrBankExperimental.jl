```
ring2nest!(m_nest_dst::HealpixMap{T, NestedOrder, AAN},
           m_ring_src::HealpixMap{T, RingOrder, AAR}) where {T, AAR, AAN}
```

Convert a map from ring to nested order. This version takes a nested map in the second argument and writes it to the nested map provided in the first argument, following the standard Julia `func!(dst, src)` convention.

# Arguments:

  * `m_nest_dst::HealpixMap{T, NestedOrder, AAN}`: map of type `RingOrder`
  * `m_ring_src::HealpixMap{T, RingOrder, AA}`: map of type `RingOrder`

# Returns:

  * `HealpixMap{T, NestedOrder, AA}`: the input map converted to `NestedOrder`

# Examples

```julia-repl
julia> m_ring = HealpixMap{Float64,RingOrder}(rand(nside2npix(64)));

julia> m_nest = HealpixMap{Float64,RingOrder}(64);

julia> ring2nest!(m_nest, m_ring)
49152-element HealpixMap{Float64, NestedOrder, Vector{Float64}}:
 0.0673134062168923
 ⋮
 0.703460503535335
```
