```
kernel_tau_bose(ω::T, τ::T, β::T) where {T<:AbstractFloat}
```

The imaginary time bosonic kernel

$$
\begin{align*}
K_\beta(\omega,\tau) & = \overbrace{\left(\frac{e^{-\tau\omega}}{1-e^{-\beta\omega}}\right)}^{\text{numerically unstable}} \\
                     & = \underbrace{\left( e^{\tau\omega} - e^{(\tau-\beta)\omega} \right)^{-1}}_{\text{numerically stable}},
\end{align*}
$$

where it is assumed that $\tau \in [0,\beta)$.
