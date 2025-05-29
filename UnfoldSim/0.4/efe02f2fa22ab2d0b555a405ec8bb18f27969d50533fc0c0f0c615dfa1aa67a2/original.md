```
generate_events(design::AbstractDesign)
generate_events(rng::AbstractRNG, design::AbstractDesign)
```

Generate a full-factorial events DataFrame based on the experimental conditions and covariates defined in the design.

# Arguments

  * `design::AbstractDesign`: Experimental design for which the events DataFrame should be created.
  * `rng::AbstractRNG` (optional): Random number generator (RNG) to make the process reproducible. If none is given, `MersenneTwister(1)` will be used.

# Returns

  * `DataFrame`: Each row corresponds to one combination of condition/covariate levels which is often equivalent to one stimulus or trial.
