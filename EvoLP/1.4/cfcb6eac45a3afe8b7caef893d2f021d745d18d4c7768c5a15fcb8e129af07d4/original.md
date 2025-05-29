```
GA(f, pop, k_max, S, C, M)
GA(logbook::Logbook, f, population, k_max, S, C, M)
GA(notebooks::Vector{Logbook}, f, population, k_max, S, C, M)
```

Generational Genetic Algorithm.

## Arguments

  * `f::Function`: objective function to **minimise**.
  * `population::AbstractVector`: a list of vector individuals.
  * `k_max::Integer`: number of iterations.
  * `S::ParentSelector`: one of the available [`ParentSelector`](@ref).
  * `C::CrossoverMethod`: one of the available [`CrossoverMethod`](@ref).
  * `M::MutationMethod`: one of the available [`MutationMethod`](@ref).

Returns a [`Result`](@ref).
