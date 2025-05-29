```
simulate_onsets(rng, onset::AbstractOnset, simulation::Simulation)
```

Call `simulate_interonset_distances` to generate distances between events and then add them up to generate the actual latencies in samples.

Please note that this function is mainly for internal use in the context of `simulate` function calls. 

Also note that the accumulation of onsets starts at 1 to avoid indexing problems in the case that the first sampled onset is 0.

# Arguments

  * `rng`: Random number generator (RNG) to make the process reproducible.
  * `onset::AbstractOnset`: Inter-onset distance distribution which is passed to `simulate_interonset_distances`.
  * `simulation::Simulation`: Simulation object which contains design, component(s), inter-onset distance distribution and noise.

# Returns

# Examples

```julia-repl
# Create Simulation object
julia> design_single = SingleSubjectDesign(;
           conditions = Dict(
               :stimulus_type => ["natural", "artificial"],
               :contrast_level => range(0, 1, length = 3),
           ),
       );

julia> p1_component = LinearModelComponent(; basis = p100(), formula = @formula(0 ~ 1), β = [5]);

julia> simulation = Simulation(design_single, p1_component, UniformOnset(), NoNoise());

julia> using StableRNGs

# Simulate onsets for this simulation
julia> simulate_onsets(StableRNG(1), simulation.onset, simulation)
6-element Vector{Int64}:
  20
  70
  97
 110
 150
 182
```

See also [`simulate_interonset_distances`](@ref).
