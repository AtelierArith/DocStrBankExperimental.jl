```
kernel_tau_sym_bose_alt(ω::T, τ::T, β::T) where {T<:AbstractFloat}
```

虚時間対称化ボースカーネル

$$
\begin{align*}
K_\beta(\omega,\tau) & = \overbrace{\omega \left(\frac{e^{-\tau\omega} + e^{-(\beta-\tau)\omega}}{1-e^{-\beta\omega}}\right)}^\text{数値的に不安定} \\
& = \underbrace{\omega\left[\left( e^{\tau\omega} - e^{(\tau-\beta)\omega} \right)^{-1} - \left(e^{-\tau\omega} - e^{-(\tau-\beta)\omega} \right)^{-1}\right]}_{\text{数値的に安定}},
\end{align*}
$$

ここで、$\tau \in [0,\beta)$ と仮定し、$K_\beta(0,\tau) = 2/\beta$ です。
