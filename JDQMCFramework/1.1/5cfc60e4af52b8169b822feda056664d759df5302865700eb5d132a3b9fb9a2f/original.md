```
stabilize_unequaltime_greens!(
    Gτ0::AbstractMatrix{T},
    G0τ::AbstractMatrix{T},
    Gττ::AbstractMatrix{T},
    G00::AbstractMatrix{T},
    logdetG::E, sgndetG::T,
    fgc::FermionGreensCalculator{T,E},
    B::AbstractVector{P};
    # KEYWORD ARGUMENTS
    update_B̄::Bool=true
)::Tuple{E,T,E,E} where {T, E, P<:AbstractPropagator{T}}
```

Stabilize the Green's function matrice $G(\tau,0)$, $G(0,\tau),$ $G(\tau,\tau)$ and $G(0,0)$ while iterating through imaginary time $\tau = \Delta\tau \cdot l.$ For a given imaginary time slice `fgc.l`, this routine should be called *after* all changes to the $B_l$ propagator have been made. When iterating through imaginary time in the forwards direction (`fgc.forward = true`), this function re-computes

$$
\begin{align}
G(\tau,0)    = & [B^{-1}(\tau,0) + B(\beta,\tau)]^{-1} \\
G(0, \tau)   = & [B^{-1}(\beta,\tau) + B(\tau,0)]^{-1} \\
G(\tau,\tau) = & [I + B(\tau,0)B(\beta,\tau)]^{-1} \\
G(0, 0)      = & [I + B(\beta,\tau)B(\tau,0)]^{-1} \\
\end{align}
$$

when at imaginary time slice `fgc.l` every `fgc.n_stab` imaginary time slice. When iterating through imaginary time in the reverse direction (`fgc.forward = false`), this function instead re-computes

$$
\begin{align*}
G(\tau-\Delta\tau,0)               = & [B^{-1}(\tau-\Delta\tau,0) + B(\beta,\tau-\Delta\tau)]^{-1} \\
G(0,\tau-\Delta\tau)               = & [B^{-1}(\beta,\tau-\Delta\tau) + B(\tau-\Delta\tau,0)]^{-1} \\
G(\tau-\Delta\tau,\tau-\Delta\tau) = & [I + B(\tau-\Delta\tau,0)B(\beta,\tau-\Delta\tau)]^{-1} \\
G(0,0)                             = & [I + B(\beta,\tau-\Delta\tau)B(\tau-\Delta\tau,0)]^{-1}
\end{align*}
$$

for `fgc.l`.

This method returns four values. The first two values returned are $\log(\vert \det G(\tau,\tau) \vert)$ and $\textrm{sign}(\det G(\tau,\tau))$. The latter two are the maximum error in a Green's function corrected by numerical stabilization $\vert \delta G \vert$, and the error in the phase of the determinant corrected by numerical stabilization $\delta\theta,$ relative to naive propagation of the Green's function matrix in imaginary time occuring instead. If no stabilization was performed, than $\vert \delta G \vert = 0$ and $\delta \theta = 0.$

This method also computes the LDR matrix factorizations representing $B(\tau, 0)$ or $B(\beta, \tau-\Delta\tau)$ when iterating through imaginary time $\tau = \Delta\tau \cdot l$ in the forward and reverse directions respectively. If `update_B̄ = true`, then the $\bar{B}_n$ matrices are re-calculated as needed, but if `update_B̄ = false,` then they are left unchanged.
