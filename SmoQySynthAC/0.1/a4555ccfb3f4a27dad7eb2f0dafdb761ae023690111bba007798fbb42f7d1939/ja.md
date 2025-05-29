```
kernel_mat_fermi(ω::T, n::Int, β::T) where {T<:AbstractFloat}
```

フェルミオンのマツバラ周波数カーネル

$$
K_\beta(\omega, \omega_n) = \frac{1}{{\omega - {\rm i}\omega_n}},
$$

ここで、$\omega_n = (2n+1)\pi/\beta$ は、$n \in \mathbb{Z}$ のフェルミオンに対してです。
