```
hellinger_dist(ρ::QuantumObject, σ::QuantumObject)
```

Calculates the [Hellinger distance](https://en.wikipedia.org/wiki/Hellinger_distance) between two [`QuantumObject`](@ref): $D_H(\hat{\rho}, \hat{\sigma}) = \sqrt{2 - 2 \textrm{Tr}\left(\sqrt{\hat{\rho}}\sqrt{\hat{\sigma}}\right)}$

Note that `ρ` and `σ` must be either [`Ket`](@ref) or [`Operator`](@ref).

# References

  * [Spehner2017](@citet)
