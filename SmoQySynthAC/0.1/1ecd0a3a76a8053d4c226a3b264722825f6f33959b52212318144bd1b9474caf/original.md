```
kernel_mat_sym_bose(ω::T, n::Int, β::T) where {T<:AbstractFloat}
```

The symmetrized bosonic matsubara frequency kernel

$$
\begin{align*}
K_β(\omega, \omega_n) & = \frac{2\omega}{\omega_n^2 + \omega^2},
\end{align*}
$$

where $\omega_n = 2n\pi/\beta$ for bosons with $n \in \mathbb{Z}$.
