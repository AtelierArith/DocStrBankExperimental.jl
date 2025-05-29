```
AsymExactPropagator{T, E} <: AbstractExactPropagator{T,E}
```

Represents imaginary time propagator matrix as using the symmetric form

$$
B_l = e^{-\Delta\tau V_l} e^{-\Delta\tau K_l},
$$

where $K_l$ is the strictly off-diagonal hopping matrix and $V_l$ is the diagonal total on-site energy matrix.

# Fields

  * `expmΔτV::Vector{E}`: A vector representing the diagonal exponeniated on-site energy matrix $e^{-\Delta\tau V_l}.$
  * `expmΔτK::Matrix{T}`: The exponentiated hopping matrix $e^{-\Delta\tau K_l}.$
  * `exppΔτK::Matrix{T}`: Inverse of the exponentiated hopping matrix $e^{+\Delta\tau K_l}.$
