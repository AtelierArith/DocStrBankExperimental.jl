```
SymExactPropagator{T, E} <: AbstractExactPropagator{T,E}
```

Represents imaginary time propagator matrix as using the symmetric form

$$
B_l = e^{-\Delta\tau K_l/2} e^{-\Delta\tau V_l} e^{-\Delta\tau K_l/2},
$$

where $K_l$ is the strictly off-diagonal hopping matrix and $V_l$ is the diagonal total on-site energy matrix.

# Fields

  * `expmΔτV::Vector{E}`: A vector representing the diagonal exponeniated on-site energy matrix $e^{-\Delta\tau V_l}.$
  * `expmΔτKo2::Matrix{T}`: The exponentiated hopping matrix $e^{-\Delta\tau K_l/2}.$
  * `exppΔτKo2::Matrix{T}`: Inverse of the exponentiated hopping matrix $e^{+\Delta\tau K_l/2}.$
