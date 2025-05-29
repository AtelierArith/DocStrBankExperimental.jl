```julia
train!(
    art::AdaptiveResonance.ART,
    x::AbstractMatrix{T} where T<:Real;
    y,
    preprocessed
) -> Any

```

# Summary

Train the ART model on a batch of data 'x' with optional supervisory labels 'y.'

# Arguments

  * `art::ART`: the unsupervised ART model to train.
  * `x::RealMatrix`: the 2-D dataset containing columns of samples with rows of features.
  * `y::IntegerVector=Int[]`: optional, labels for simple supervisory training.
  * `preprocessed::Bool=false`: optional, flag if the data has already been complement coded or not.

# Method List / Definition Locations

```julia
train!(art, x; y, preprocessed)
```

defined at [`packages/AdaptiveResonance/wgSPV/src/ART/common.jl:21`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/ART/common.jl).
