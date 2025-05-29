```
NN(params::Parameters;
    architecture::Union{Flux.Chain, Nothing} = nothing,
    θ::Union{Vector{AbstractFloat}, Nothing} = nothing)
```

Creates a new feed-forward neural network.

# Keyword arguments

  * `architecture`: `Flux.Chain` neural network architecture (optional)
  * `θ`: Neural network parameters (optional)
