```
kernel_mat(ω::T, ω_n::T) where {T<:AbstractFloat}
```

一般的なマツバラ周波数カーネル

$$
K_\beta(\omega, \omega_n) = \frac{1}{\omega - {\rm i}\omega_n},
$$

ここで、$\omega_n = (2n+1)\pi/\beta \ (= 2n\pi/\beta)$ はフェルミオン（ボソン）のためのもので、$n \in \mathbb{Z}$ です。このカーネルは次の符号規約を仮定します。

$$
C(\tau) = \langle \hat{a}(\tau) \hat{a}^\dagger(0) \rangle
$$

ここで、$a$ はグリーン関数であり、$\tau \in [0,\beta)$ であると仮定されています。
