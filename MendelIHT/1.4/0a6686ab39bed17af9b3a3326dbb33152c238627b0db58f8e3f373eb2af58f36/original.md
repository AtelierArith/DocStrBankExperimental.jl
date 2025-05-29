```
project_k!(x::AbstractVector, k::Integer)
```

Sets all but the largest `k` entries of `x` to 0. 

# Examples:

```julia-repl
using MendelIHT
x = [1.0; 2.0; 3.0]
project_k!(x, 2) # keep 2 largest entry
julia> x
3-element Array{Float64,1}:
 0.0
 2.0
 3.0
```

# Arguments:

  * `x`: the vector to project.
  * `k`: the number of components of `x` to preserve.
