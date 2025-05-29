```
kernel_mat_fermi(ω::T, n::Int, β::T) where {T<:AbstractFloat}
```

The fermionic matsubara frequency kernel

$$
K_\beta(\omega, \omega_n) = \frac{1}{{\omega - {\rm i}\omega_n}},
$$

where $\omega_n = (2n+1)\pi/\beta$ for fermions with $n \in \mathbb{Z}$.
