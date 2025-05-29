```
simulate_interonset_distances(rng, onset::AbstractOnset, design::AbstractDesign)
```

Generate the inter-onset distance vector by sampling from the respective distribution (in samples).

# Arguments

  * `rng`: Random number generator (RNG) to make the process reproducible.
  * `onset::AbstractOnset`: Inter-onset distance distribution to sample from.
  * `design::AbstractDesign`: Experimental design with conditions and covariates.

# Returns

  * `Vector{Integer}`: Inter-onset distances in samples. Note that these are distances between onsets and no latencies.

# Examples

```julia-repl
# Create an experimental design
julia> design_single = SingleSubjectDesign(;
           conditions = Dict(
               :stimulus_type => ["natural", "artificial"],
               :contrast_level => range(0, 1, length = 3),
           ),
       );

# Create an inter-onset distance distribution
julia> onset_distribution = LogNormalOnset(3, 0.5, 5, nothing);

julia> using StableRNGs

julia> simulate_interonset_distances(StableRNG(1), onset_distribution, design_single)
6-element Vector{Int64}:
 20
 26
 34
 18
 12
 23
```

See also [`simulate_onsets`](@ref).
