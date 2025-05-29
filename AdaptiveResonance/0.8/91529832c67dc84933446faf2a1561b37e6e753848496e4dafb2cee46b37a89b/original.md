# Summary

Predict categories of a single sample of features 'x' using the ART model.

Returns predicted category 'y_hat.'

# Arguments

  * `art::ARTModule`: ART or ARTMAP module to use for batch inference.
  * `x::RealVector`: the single sample of features to classify.
  * `preprocessed::Bool=false`: optional, flag if the data has already been complement coded or not.
  * `get_bmu::Bool=false`: optional, flag if the model should return the best-matching-unit label in the case of total mismatch.

# Method List / Definition Locations

```julia
classify(art, x; preprocessed, get_bmu)
```

defined at [`packages/AdaptiveResonance/wgSPV/src/ART/distributed/modules/DDVFA.jl:362`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/ART/distributed/modules/DDVFA.jl).

```julia
classify(art, x; preprocessed, get_bmu)
```

defined at [`packages/AdaptiveResonance/wgSPV/src/ART/single/modules/DVFA.jl:360`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/ART/single/modules/DVFA.jl).

```julia
classify(art, x; preprocessed, get_bmu)
```

defined at [`packages/AdaptiveResonance/wgSPV/src/ART/single/modules/FuzzyART.jl:392`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/ART/single/modules/FuzzyART.jl).

```julia
classify(art, x; preprocessed, get_bmu)
```

defined at [`packages/AdaptiveResonance/wgSPV/src/ARTMAP/SFAM.jl:315`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/ARTMAP/SFAM.jl).
