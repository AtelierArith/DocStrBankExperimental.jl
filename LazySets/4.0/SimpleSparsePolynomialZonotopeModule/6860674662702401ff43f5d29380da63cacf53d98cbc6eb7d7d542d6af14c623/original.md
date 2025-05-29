# Extended help

```
rand(::Type{SimpleSparsePolynomialZonotope};
     [N]::Type{<:Real}=Float64, [dim]::Int=2, [nparams]::Int=2,
     [maxdeg]::Int=3, [num_generators]::Int=-1,
     [rng]::AbstractRNG=GLOBAL_RNG, [seed]::Union{Int, Nothing}=nothing)
```

### Algorithm

All numbers are normally distributed with mean 0 and standard deviation 1.

The number of generators can be controlled with the argument `num_generators`. For a negative value we choose a random number in the range `dim:2*dim` (except if `dim == 1`, in which case we only create a single generator). Note that the final number of generators may be lower if redundant monomials are generated.
