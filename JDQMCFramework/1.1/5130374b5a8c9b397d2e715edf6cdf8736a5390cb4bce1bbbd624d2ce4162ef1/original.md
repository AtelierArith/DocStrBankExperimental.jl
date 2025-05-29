```
propagate_equaltime_greens!(
    G::AbstractMatrix{T},
    fgc::FermionGreensCalculator{T,E},
    B::AbstractVector{P}
) where {T, E, P<:AbstractPropagator{T}}
```

Propagate the equal-time Green's function matrix `G` from the previous imaginary time slice to the current imaginary time slice `fgc.l`. If iterating over imaginary time in the forward direction (`fgc.forward = true`) the relationship

$$
G(\tau+\Delta\tau,\tau+\Delta\tau) = B_{l+1} \cdot G(\tau,\tau) \cdot B_{l+1}^{-1}
$$

is used, and if iterating over imaginary time in the reverse direction (`fgc.forward = false`) the relationship

$$
G(\tau-\Delta\tau,\tau-\Delta\tau)= B_{l}^{-1} \cdot G(\tau,\tau) \cdot B_{l}
$$

is used instead, where the $B_l$ propagator is given by `B[l]`.
