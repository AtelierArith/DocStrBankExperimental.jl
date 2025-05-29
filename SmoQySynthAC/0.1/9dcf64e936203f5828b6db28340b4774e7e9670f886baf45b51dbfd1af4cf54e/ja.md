```
kernel_tau_fermi(ω::T, τ::T, β::T) where {T<:AbstractFloat}
```

虚時間フェルミオンカーネル

$$
\begin{align*}
K_\beta(\omega,\tau) & = \overbrace{\left(\frac{e^{-\tau\omega}}{1+e^{-\beta\omega}}\right)}^{\text{数値的に不安定}} \\
                     & = \underbrace{\left( e^{\tau\omega} + e^{(\tau-\beta)\omega} \right)^{-1}}_{\text{数値的に安定}},
\end{align*}
$$

ここで、$\tau \in [0,\beta)$であると仮定されます。
