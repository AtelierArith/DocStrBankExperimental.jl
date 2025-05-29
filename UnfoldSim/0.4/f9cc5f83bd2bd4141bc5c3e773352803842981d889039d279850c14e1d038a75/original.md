```
simulate_responses(
    rng,
    components::Vector{<:AbstractComponent},
    simulation::Simulation)
```

Simulate multiple component responses and accumulate them on a per-event basis.

# Returns

  * `epoch_data`: `Matrix` (or `Array` in the multi-channel case) of combined simulated components.   The output dimensions are `maxlength(components) x length(simulation.design)` for single-channel components and   `n_channels(components) x maxlength(components) x length(simulation.design)` for multi-channel components.

# Examples

```julia-repl
julia> design = SingleSubjectDesign(; conditions = Dict(:cond => ["natural", "artificial"]));

julia> c1 = LinearModelComponent(; basis = p100(), formula = @formula(0 ~ 1 + cond), β = [1, 0.5]);
julia> c2 = LinearModelComponent(; basis = p300(), formula = @formula(0 ~ 1), β = [2]);

julia> simulation = Simulation(design, [c1, c2], UniformOnset(; width = 0, offset = 30), PinkNoise());

julia> using StableRNGs

julia> simulate_responses(StableRNG(1), [c1, c2], simulation)
45×2 Matrix{Float64}:
 0.0        0.0
 0.0        0.0
 0.0        0.0
 0.0        0.0
 0.0        0.0
 ⋮          
 0.352614   0.352614
 0.203907   0.203907
 0.0924246  0.0924246
 0.0233794  0.0233794
 0.0        0.0
```
