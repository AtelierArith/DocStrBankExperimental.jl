```
partially_wrap_greens_forward!(
    G::Matrix{T},
    B::P,
    M::Matrix{T} = similar(G)
) where {T, E, P<:AbstractPropagator{T,E}}
```

If the propagator `B` is represented in the symmetric form

$$
B_l = \Gamma_l(\Delta\tau/2) \cdot \Lambda_l(\Delta\tau) \cdot \Gamma_l^\dagger(\Delta\tau/2)
$$

with $\tau = l \cdot \Delta\tau,$ where $\Gamma(\Delta\tau/2) = e^{-\Delta\tau K_l/2}$ and $\Lambda(\Delta\tau) = e^{-\Delta\tau V_l}$, then apply the transformation

$$
\tilde{G}(\tau,\tau) = \Gamma^{-1}_l(\Delta\tau/2) \cdot G(\tau,\tau) \cdot \Gamma_l(\Delta\tau/2)
$$

to the equal-time Green's function matrix `G` in-place.
