```
constrained_dimensions(HS::HybridSystem)::Dict{Int,Vector{Int}}
```

For each location, compute all dimensions that are constrained in the invariant or the guard of any outgoing transition.

### Input

  * `HS`  – hybrid system

### Output

A dictionary mapping (`::Dict{Int,Vector{Int}}`) the index of each location $ℓ$ to the dimension indices that are constrained in $ℓ$.
