```julia
GetQIndex(Q::Vector{Float64}, bz::BZ ; nearest::Bool = false) --> Vector{Int64}
```

Returns the index in the discretized `BZ` of the momentum point corresponding to the fiven momentum `Q`.  If the input `nearest` is set to `true`, will return the index of the momentum point on the grid closest to `Q`, if `Q` does not exist on the grid. 
