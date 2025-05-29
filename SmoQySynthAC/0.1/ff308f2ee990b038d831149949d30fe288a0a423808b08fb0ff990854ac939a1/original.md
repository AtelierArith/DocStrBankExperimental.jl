```
kernel_mat(ω::T, ω_n::T) where {T<:AbstractFloat}
```

Generic Matsubara frequency kernel

$$
K_\beta(\omega, \omega_n) = \frac{1}{\omega - {\rm i}\omega_n},
$$

where $\omega_n = (2n+1)\pi/\beta \ (= 2n\pi/\beta)$ for fermions (bosons) with $n \in \mathbb{Z}$. This kernel assumes the sign convention

$$
C(\tau) = \langle \hat{a}(\tau) \hat{a}^\dagger(0) \rangle
$$

for a the Green's function, where it is assumed that $\tau \in [0,\beta)$.
