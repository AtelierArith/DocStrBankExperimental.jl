```
kernel_mat_bose_alt(ω::T, n::Int, β::T) where {T<:AbstractFloat}
```

ボソニックマツバラ周波数カーネル

$$
K_\beta(\omega, \omega_n) = \frac{\omega}{\omega - {\rm i}\omega_n},
$$

ここで、$\omega_n = 2n\pi/\beta$ はボソンに対して $n \in \mathbb{Z}$ であり、$K_\beta(0,0) = -1$ です。
