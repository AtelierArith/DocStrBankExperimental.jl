```
PSDArch <: SymplecticCompression
```

`PSDArch` is the architecture that corresponds to [`PSDLayer`](@ref). 

## The architecture

Proper symplectic decomposition (PSD) can be seen as a [`SymplecticAutoencoder`](@ref) for which the decoder and the encoder are both PSD-like matrices (see the docs for [`PSDLayer`](@ref). 

## Training

For optimizing the parameters in this architecture no neural network training is necessary (see the docs for [`solve!`](@ref)).

## The constructor

The constructor only takes two arguments as input:

  * `full_dim::Integer`
  * `reduced_dim::Integer`
