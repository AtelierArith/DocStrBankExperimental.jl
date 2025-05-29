```
polysidelengths(p::Vector{Point}; closed = true)
```

Return an array containing the lengths of each "side" of the polygon `p`.

If `closed = false`, the side joining the last point to the first is not included.

```julia
polysidelengths(ngon(O, 100, 4))
4-element Vector{Float64}:
 141.42135623730948
 141.4213562373095
 141.4213562373095
 141.42135623730954

polysidelengths(ngon(O, 100, 4), closed=false)
3-element Vector{Float64}:
 141.42135623730948
 141.4213562373095
 141.4213562373095
```
