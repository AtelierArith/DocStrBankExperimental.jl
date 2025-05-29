```julia
train!(
    art::AdaptiveResonance.ARTMAP,
    x::AbstractMatrix{T} where T<:Real,
    y::AbstractVector{T} where T<:Integer
) -> Any
train!(
    art::AdaptiveResonance.ARTMAP,
    x::AbstractMatrix{T} where T<:Real,
    y::AbstractVector{T} where T<:Integer,
    preprocessed::Bool
) -> Any

```

# Summary

```
train!(art::ARTMAP, x::RealMatrix, y::IntegerVector, preprocessed::Bool=false)
```

Train the ARTMAP model on a batch of data 'x' with supervisory labels 'y.'

# Arguments

  * `art::ARTMAP`: the supervised ARTMAP model to train.
  * `x::RealMatrix`: the 2-D dataset containing columns of samples with rows of features.
  * `y::IntegerVector`: labels for supervisory training.
  * `preprocessed::Bool=false`: flag, if the data has already been complement coded or not.

# Method List / Definition Locations

```julia
train!(art, x, y)
train!(art, x, y, preprocessed)
```

defined at [`packages/AdaptiveResonance/wgSPV/src/ARTMAP/common.jl:23`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/ARTMAP/common.jl).
