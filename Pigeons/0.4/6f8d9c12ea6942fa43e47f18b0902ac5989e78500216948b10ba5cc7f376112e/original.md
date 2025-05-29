```julia
toy_mvn_target(dim)

```

A toy multi-variate normal (mvn) target distribution used for testing. Uses a specialized path, [`ScaledPrecisionNormalPath`](@ref), such that i.i.d. sampling is possible at all chains (via [`ToyExplorer`](@ref)).
