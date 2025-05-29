```
simulate_component(rng, c::MixedModelComponent, design::AbstractDesign, return_parameters = false)
```

Generate a MixedModel and simulate data according to the given parameters `c.β` and `c.σs`.

# Keyword arguments

  * `return_parameters::Bool = false`: Can be used to return the per-event parameters used to weight the basis function. Sometimes useful to inspect what is simulated.

# Returns

  * `Matrix{Float64}`: Simulated component for each event in the events data frame. The output dimensions are `length(c.basis) x length(design)`.

# Notes

1. MixedModels/Sim does not allow simulation of data without white noise of the residuals. Because we want our own noise, we use the following trick to remove the MixedModels-Noise:

Practically, we upscale the specified `σs` by factor 10*000, and request a white-noise-level of `σ = 0.0001`. Internally in MixedModels/Sim, `σs` are relative to `σ`, and thus are normalized correctly, while keeping the noise 10*000 times smaller than the random effects

We cannot exclude that this trick runs into strange numerical issues if the random effect `σs` are very large compared to the fixed effects.

2. Currently, it is not possible to use a different basis for fixed and random effects. If this is needed, some code-scaffold is available but commented out at the moment and requires a bit of implementation work.

# Examples

```julia-repl
julia> design = MultiSubjectDesign(; n_subjects = 2, n_items = 6, items_between = Dict(:cond => ["A", "B"]));

julia> c = UnfoldSim.MixedModelComponent([0, 1, 1, 0], @formula(0 ~ 1 + cond + (1|subject)), [1, 2], Dict(:subject => [2],), Dict());

julia> using StableRNGs

julia> simulate_component(StableRNG(1), c, design)
4×12 Matrix{Float64}:
 -0.0      -0.0       -0.0      -0.0       -0.0     -0.0       0.0       0.0      0.0       0.0      0.0       0.0
 -2.70645  -0.706388  -2.70632  -0.706482  -2.7066  -0.706424  0.325722  2.32569  0.325627  2.32564  0.325468  2.32565
 -2.70645  -0.706388  -2.70632  -0.706482  -2.7066  -0.706424  0.325722  2.32569  0.325627  2.32564  0.325468  2.32565
 -0.0      -0.0       -0.0      -0.0       -0.0     -0.0       0.0       0.0      0.0       0.0      0.0       0.0

julia> simulate_component(StableRNG(1), c, design, return_parameters = true)
1×12 Matrix{Float64}:
 -2.70645  -0.706388  -2.70632  -0.706482  -2.7066  -0.706424  0.325722  2.32569  0.325627  2.32564  0.325468  2.32565
```
