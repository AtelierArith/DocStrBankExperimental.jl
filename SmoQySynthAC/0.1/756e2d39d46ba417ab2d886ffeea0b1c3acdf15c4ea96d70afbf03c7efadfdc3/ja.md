```
kernel_tau_bose_alt(ω::T, τ::T, β::T) where {T<:AbstractFloat}
```

虚時間ボソニックカーネル

$$
\begin{align*}
K_\beta(\omega,\tau) & = \overbrace{\left(\frac{\omega e^{-\tau\omega}}{1-e^{-\beta\omega}}\right)}^{\text{数値的に不安定}} \\
                     & = \underbrace{\omega \left( e^{\tau\omega} - e^{(\tau-\beta)\omega} \right)^{-1}}_{\text{数値的に安定}},
\end{align*}
$$

ここで、$\tau \in [0,\beta)$ と仮定し、$K_\beta(0,\tau) = \beta^{-1}$ です。
