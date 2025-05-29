```julia
FuzzyART(
    opts::AdaptiveResonance.opts_FuzzyART,
    sample::AbstractVector{T} where T<:Real;
    preprocessed
) -> AdaptiveResonance.FuzzyART

```

# Summary

Create and initialize a FuzzyART with a single sample in one step.

Principally used as a method for initialization within DDVFA.

# Arguments

  * `opts::opts_FuzzyART`: the FuzzyART options contains.
  * `sample::RealVector`: the sample to use as a basis for setting up the FuzzyART.
  * `preprocessed::Bool=false`: flag for if the sample is already complement coded and normalized.

# Method List / Definition Locations

```julia
FuzzyART(opts, sample; preprocessed)
```

defined at [`packages/AdaptiveResonance/wgSPV/src/ART/single/modules/FuzzyART.jl:247`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/ART/single/modules/FuzzyART.jl).
