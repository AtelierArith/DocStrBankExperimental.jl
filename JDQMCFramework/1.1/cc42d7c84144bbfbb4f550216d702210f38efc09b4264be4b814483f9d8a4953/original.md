```
local_update_det_ratio(
    G::AbstractMatrix,
    B::AbstractPropagator,
    V′::T, i::Int, Δτ::E
) where {T<:Number, E<:AbstractFloat}
```

Calculate the determinant ratio $R_{l,i}$ associated with a local update to the equal-time Green's function $G(\tau,\tau).$ Also returns $\Delta_{l,i},$ which is defined below. Specifically, this function returns the tuple $(R_{l,i}, \Delta_{l,i})$.

# Arguments

  * `G::AbstractMatrix`: Equal-time Green's function matrix $G(\tau,\tau).$
  * `B::AbstractPropagator`: Represents the propagator matrix $B_l,$ where $\tau = \Delta\tau \cdot l.$
  * `V′::T`: The new value for the $V^{\prime}_{l,i,i}$ matrix element in the diagonal on-site energy matrix $V_l.$
  * `i::Int`: Diagonal matrix element index in $V_l$ being updated.
  * `Δτ::E`: Discretization in imaginary time $\Delta\tau.$

# Algorithm

The propagator matrix $B_l$ above is given by

$$
B_l = \Lambda_l \cdot \Gamma_l(\Delta\tau),
$$

where, assuming the we are working in the orbital basis, $\Gamma_l(\Delta\tau) = e^{-\Delta\tau K_l}$ represents the exponentiated hopping matrix $K_l$, and $\Lambda_l = e^{-\Delta\tau V_l}$ represents the exponentiated diagonal on-site energy matrix $V_l.$

Given a proposed update to the $(i,i)$ matrix element of the diagonal on-site energy matrix $V_l$, ($V_{l,i,i} \rightarrow V^\prime_{l,i,i}),$ the corresponding determinant ratio associated with this proposed udpate is given by

$$
R_{l,i} = \frac{\det G(\tau,\tau)}{\det G^\prime(\tau,\tau)} = 1+\Delta_{i,i}(\tau,i)\left(1-G_{i,i}(\tau,\tau)\right),
$$

where

$$
\Delta_{l,i} = \frac{\Lambda^\prime_{l,i,i}}{\Lambda_{l,i,i}} - 1 = e^{-\Delta\tau (V^\prime_{l,i,i} - V_{l,i,i})} - 1.
$$

This routine returns the scalar quantities $R_{l,i}$ and $\Delta_{l,i}.$

Note that if the propagator matrix is instead represented using the symmetric form

$$
B_l = \Gamma_l(\Delta\tau/2) \cdot \Lambda_l \cdot \Gamma^\dagger_l(\Delta\tau/2),
$$

then the matrix `G` needs to instead represent the transformed equal-time Green's function matrix

$$
\tilde{G}(\tau,\tau) = \Gamma_l^{-1}(\Delta\tau/2) \cdot G(\tau,\tau) \cdot \Gamma_l(\Delta\tau/2).
$$
