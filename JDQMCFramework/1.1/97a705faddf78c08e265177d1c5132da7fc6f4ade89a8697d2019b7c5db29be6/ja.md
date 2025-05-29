```
initialize_unequaltime_greens!(
    Gτ0::AbstractMatrix{T},
    G0τ::AbstractMatrix{T},
    Gττ::AbstractMatrix{T},
    G00::AbstractMatrix{T}
) where {T<:Number}
```

$$
\tau = 0
$$

のときの行列 $G(0,0)$ に基づいて、グリーン関数行列 $G(\tau,0),$ $G(0,\tau),$ および $G(\tau,\tau)$ を初期化します。
