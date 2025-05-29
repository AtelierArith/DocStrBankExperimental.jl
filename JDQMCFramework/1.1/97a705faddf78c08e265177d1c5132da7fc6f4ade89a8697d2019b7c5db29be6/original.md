```
initialize_unequaltime_greens!(
    Gτ0::AbstractMatrix{T},
    G0τ::AbstractMatrix{T},
    Gττ::AbstractMatrix{T},
    G00::AbstractMatrix{T}
) where {T<:Number}
```

Initialize the Green's function matrices $G(\tau,0),$ $G(0,\tau),$ and $G(\tau,\tau)$ for $\tau = 0$ based on the matrix $G(0,0).$
