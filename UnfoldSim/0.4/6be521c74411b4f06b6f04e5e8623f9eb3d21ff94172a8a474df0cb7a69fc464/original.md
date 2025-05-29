```
simulate_component(rng, c::LinearModelComponent, design::AbstractDesign)
```

Generate a linear model design matrix, weight it by the coefficients `c.β` and multiply the result with the given basis vector.

# Returns

  * `Matrix{Float64}`: Simulated component for each event in the events data frame. The output dimensions are `length(c.basis) x length(design)`.

# Examples

```julia-repl
julia> design = SingleSubjectDesign(; conditions = Dict(:cond => ["natural", "artificial"]));

julia> c = UnfoldSim.LinearModelComponent([0, 1, 1, 0], @formula(0 ~ 1 + cond), [1, 2], Dict());

julia> using StableRNGs

julia> simulate_component(StableRNG(1), c, design)
4×2 Matrix{Float64}:
 0.0  0.0
 3.0  1.0
 3.0  1.0
 0.0  0.0
```
