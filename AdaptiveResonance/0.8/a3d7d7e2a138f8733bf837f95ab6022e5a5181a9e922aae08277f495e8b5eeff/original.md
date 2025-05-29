# Summary

Train the supervised ARTMAP model on a single sample of features 'x' with supervisory label 'y'.

# Arguments

  * `art::ARTMAP`: the supervised ART model to train.
  * `x::RealVector`: the single sample feature vector to train upon.
  * `y::Integer`: the label for supervisory training.
  * `preprocessed::Bool=false`: optional, flag if the data has already been complement coded or not.

# Method List / Definition Locations

```julia
train!(art, x, y; preprocessed)
```

defined at [`packages/AdaptiveResonance/wgSPV/src/ARTMAP/SFAM.jl:235`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/ARTMAP/SFAM.jl).
