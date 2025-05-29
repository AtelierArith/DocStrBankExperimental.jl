# Summary

Train the ART model on a single sample of features 'x' with an optional supervisory label.

# Arguments

  * `art::ART`: the unsupervised ART model to train.
  * `x::RealVector`: the single sample feature vector to train upon.
  * `y::Integer=0`: optional, a label for simple supervisory training.
  * `preprocessed::Bool=false`: optional, flag if the data has already been complement coded or not.

# Method List / Definition Locations

```julia
train!(art, x; y, preprocessed)
```

defined at [`packages/AdaptiveResonance/wgSPV/src/ART/distributed/modules/DDVFA.jl:275`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/ART/distributed/modules/DDVFA.jl).

```julia
train!(art, x; y, preprocessed)
```

defined at [`packages/AdaptiveResonance/wgSPV/src/ART/single/modules/DVFA.jl:268`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/ART/single/modules/DVFA.jl).

```julia
train!(art, x; y, preprocessed)
```

defined at [`packages/AdaptiveResonance/wgSPV/src/ART/single/modules/FuzzyART.jl:300`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/ART/single/modules/FuzzyART.jl).
