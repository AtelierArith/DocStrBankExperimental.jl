```
kernel_tau_bose_alt(ω::T, τ::T, β::T) where {T<:AbstractFloat}
```

The imaginary time bosonic kernel

$$
\begin{align*}
K_\beta(\omega,\tau) & = \overbrace{\left(\frac{\omega e^{-\tau\omega}}{1-e^{-\beta\omega}}\right)}^{\text{numerically unstable}} \\
                     & = \underbrace{\omega \left( e^{\tau\omega} - e^{(\tau-\beta)\omega} \right)^{-1}}_{\text{numerically stable}},
\end{align*}
$$

where it is assumed that $\tau \in [0,\beta)$ and $K_\beta(0,\tau) = \beta^{-1}$.
