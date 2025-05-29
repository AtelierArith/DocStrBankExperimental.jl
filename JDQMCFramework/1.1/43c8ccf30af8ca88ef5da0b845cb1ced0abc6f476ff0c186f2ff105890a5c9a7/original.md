```
propagate_unequaltime_greens!(
    Gτ0::AbstractMatrix{T},
    G0τ::AbstractMatrix{T},
    Gττ::AbstractMatrix{T},
    fgc::FermionGreensCalculator{T,E},
    B::AbstractVector{P}
) where {T, E, P<:AbstractPropagator{T}}
```

Propagate the Green's function matrices $G(\tau,0)$, $G(0,\tau)$ and $G(\tau,\tau)$ from the previous imaginary time slice to the current imaginary time slice `fgc.l`. If iterating over imaginary time in the forward direction (`fgc.forward = true`) the relationships

$$
\begin{align}
G(\tau,0)    = & B_{l} \cdot G(\tau-\Delta\tau, 0) \\
G(0,\tau)    = & G(0, \tau-\Delta\tau) \cdot B^{-1}_{l} \\
G(\tau,\tau) = & B_{l} \cdot G(\tau-\Delta\tau, \tau-\Delta\tau) \cdot B_{l}^{-1}
\end{align}
$$

are used, and if iterating over imaginary time in the reverse direction (`fgc.forward = false`) the relationships

$$
\begin{align}
G(\tau,0)    = & B_{l+1}^{-1} \cdot G(\tau+\Delta\tau, 0) \\
G(0,\tau)    = & G(0, \tau + \Delta\tau) \cdot B_{l+1} \\
G(\tau,\tau) = & B_{l+1}^{-1} \cdot G(\tau+\Delta\tau, \tau+\Delta\tau) \cdot B_{l+1}
\end{align}
$$

are used instead, where the $B_l$ propagator is given by `B[l]`.
