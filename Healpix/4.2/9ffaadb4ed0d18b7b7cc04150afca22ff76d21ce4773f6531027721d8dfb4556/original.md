```
nest2ring(m_nest::HealpixMap{T, NestedOrder, AA}) where {T, AA}
```

Convert a map from nested to ring order. This version allocates a new array of the same array type as the input.

# Arguments:

  * `m_nest::HealpixMap{T, NestedOrder, AA}`: map of type `NestedOrder`

# Returns:

  * `HealpixMap{T, RingOrder, AA}`: the input map converted to `RingOrder`

# Examples

```julia-repl
julia> m_nest = HealpixMap{Float64,NestedOrder}(rand(nside2npix(64)));

julia> nest2ring(m_nest)
49152-element HealpixMap{Float64, RingOrder, Vector{Float64}}:
 0.4703834205807309
 ⋮
 0.3945848051663148
```
