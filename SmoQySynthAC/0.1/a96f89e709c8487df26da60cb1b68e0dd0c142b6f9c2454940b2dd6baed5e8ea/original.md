```
kernel_mat_bose(ω::T, n::Int, β::T) where {T<:AbstractFloat}
```

The bosonic matsubara frequency kernel

$$
K_\beta(\omega, \omega_n) = \frac{1}{\omega - {\rm i}\omega_n},
$$

where $\omega_n = 2n\pi/\beta$ for bosons with $n \in \mathbb{Z}$.
