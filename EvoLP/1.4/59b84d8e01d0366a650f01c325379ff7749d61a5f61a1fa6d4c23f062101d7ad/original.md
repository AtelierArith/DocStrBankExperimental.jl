```
oneplusone(f, ind, k_max, M)
oneplusone(logger::Logbook, f, ind, k_max, M)
```

1+1 Evolutionary Algorithm.

# Arguments

  * `f::Function`: objective function to **minimise**.
  * `ind::AbstractVector`: individual to start the evolution.
  * `k_max::Integer`: number of iterations.
  * `M::Mutator`: one of the available [`Mutator`](@ref).

Returns a [`Result`](@ref).
