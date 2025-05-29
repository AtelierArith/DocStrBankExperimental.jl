```
propagate_unequaltime_greens!(
    Gτ0::AbstractMatrix{T},
    G0τ::AbstractMatrix{T},
    Gττ::AbstractMatrix{T},
    fgc::FermionGreensCalculator{T,E},
    B::AbstractVector{P}
) where {T, E, P<:AbstractPropagator{T}}
```

前の虚時間スライスから現在の虚時間スライス `fgc.l` へグリーン関数行列 $G(\tau,0)$、$G(0,\tau)$、および $G(\tau,\tau)$ を伝播させます。虚時間を前方方向に反復している場合（`fgc.forward = true`）、次の関係式が使用されます。

$$
\begin{align}
G(\tau,0)    = & B_{l} \cdot G(\tau-\Delta\tau, 0) \\
G(0,\tau)    = & G(0, \tau-\Delta\tau) \cdot B^{-1}_{l} \\
G(\tau,\tau) = & B_{l} \cdot G(\tau-\Delta\tau, \tau-\Delta\tau) \cdot B_{l}^{-1}
\end{align}
$$

逆方向に虚時間を反復している場合（`fgc.forward = false`）、次の関係式が代わりに使用されます。

$$
\begin{align}
G(\tau,0)    = & B_{l+1}^{-1} \cdot G(\tau+\Delta\tau, 0) \\
G(0,\tau)    = & G(0, \tau + \Delta\tau) \cdot B_{l+1} \\
G(\tau,\tau) = & B_{l+1}^{-1} \cdot G(\tau+\Delta\tau, \tau+\Delta\tau) \cdot B_{l+1}
\end{align}
$$

ここで、$B_l$ の伝播子は `B[l]` で与えられます。
