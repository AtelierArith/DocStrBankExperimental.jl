```
kernel_tau_sym_bose_alt(ω::T, τ::T, β::T) where {T<:AbstractFloat}
```

The imaginary time symmetrized bosonic kernel

$$
\begin{align*}
K_\beta(\omega,\tau) & = \overbrace{\omega \left(\frac{e^{-\tau\omega} + e^{-(\beta-\tau)\omega}}{1-e^{-\beta\omega}}\right)}^\text{numerically unstable} \\
& = \underbrace{\omega\left[\left( e^{\tau\omega} - e^{(\tau-\beta)\omega} \right)^{-1} - \left(e^{-\tau\omega} - e^{-(\tau-\beta)\omega} \right)^{-1}\right]}_{\text{numerically stable}},
\end{align*}
$$

where it is assumed that $\tau \in [0,\beta)$ and $K_\beta(0,\tau) = 2/\beta$.
