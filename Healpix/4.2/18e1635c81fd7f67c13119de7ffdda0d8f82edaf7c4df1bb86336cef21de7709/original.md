```
nest2ring!(m_ring_dst::HealpixMap{T, RingOrder, AAR},
           m_nest_src::HealpixMap{T, NestedOrder, AAN}) where {T, AAN, AAR}
```

Convert a map from nested to ring order. This version takes a nested map in the second argument and writes it to the nested map provided in the first argument, following the standard Julia `func!(dst, src)` convention.

# Arguments:

  * `m_ring_dst::HealpixMap{T, NestedOrder, AA}`: map of type `NestedOrder`
  * `m_nest_src::HealpixMap{T, NestedOrder, AAN}`: map of type `RingOrder`

# Returns:

  * `HealpixMap{T, RingOrder, AA}`: the input map converted to `RingOrder`

# Examples

```julia-repl
julia> m_nest = HealpixMap{Float64,NestedOrder}(rand(nside2npix(64)));

julia> m_ring = HealpixMap{Float64,RingOrder}(64);

julia> nest2ring!(m_ring, m_nest)
49152-element HealpixMap{Float64, RingOrder, Vector{Float64}}:
 0.33681791815569895
 ⋮
 0.9092457003948482
```
