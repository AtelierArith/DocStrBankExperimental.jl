```
AsymChkbrdPropagator{T, E} <: AbstractChkbrdPropagator{T,E}
```

Represents imaginary time propagator matrix as using the symmetric form

$$
B_l = e^{-\Delta\tau V_l} e^{-\Delta\tau K_l},
$$

where $K_l$ is the strictly off-diagonal hopping matrix and $V_l$ is the diagonal total on-site energy matrix. The exponentiated hopping matrix $e^{-\Delta\tau K}$ is represented by the checkerboard approximation.

# Fields

  * `expmΔτV::Vector{E}`: The vector representing the diagonal exponeniated on-site energy matrix $e^{-\Delta\tau V_l}.$
  * `expmΔτK::CheckerboardMatrix{T}`: The exponentiated hopping matrix $e^{-\Delta\tau K_l}$ represented by the checkerboard approximation.
