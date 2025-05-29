```
calculate_equaltime_greens!(
    G::AbstractMatrix{T},
    fgc::FermionGreensCalculator{T,E}
)::Tuple{E,T} where {T,E}
```

Calculate the equal-time Greens function $G(0,0) = G(\beta,\beta) = [I + B(\beta,0)]^{-1}$ using a numerically stable procedure. This method also returns $\log(\vert \det G \vert)$ and $\textrm{sign}(\det G).$ Note that this routine requires `fgc.l == 1` or `fgc.l == fgc.Lτ`.
