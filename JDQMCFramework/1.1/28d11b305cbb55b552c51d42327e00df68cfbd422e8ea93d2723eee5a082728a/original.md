```
calculate_equaltime_greens!(
    G::AbstractMatrix{T},
    fgc::FermionGreensCalculator{T,E},
    B::AbstractVector{P}
)::Tuple{E,T} where {T, E, P<:AbstractPropagator{T}}
```

Calculate the equal-time Greens function $G(0,0) = G(\beta,\beta) = [I + B(\beta,0)]^{-1}$ using a numerically stable procedure. Also re-calculate the $\bar{B}_n$ matrices and the LDR matrix factorizations representing either $B(\tau,0)$ or $B(\beta,\tau)$ stored in `fgc.F`. This routine is useful for implementing global updates where every propagator matrix $B_l$ has been modified, and the equal-time Green's function needs to be re-calculated from scratch. This method also returns $\log(\vert \det G \vert)$ and $\textrm{sign}(\det G).$ Note that this routine requires `fgc.l == 1` or `fgc.l == fgc.Lτ`.
