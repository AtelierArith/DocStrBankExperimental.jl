```
ReducedLoss(autoencoder)
```

Make an instance of `ReducedLoss` based on a neural network of type [`AutoEncoder`](@ref).

Internally this does:

```julia
ReducedLoss(encoder(autoencoder), decoder(autoencoder))
```

so it calls the functions [`encoder`](@ref) and [`decoder`](@ref).
