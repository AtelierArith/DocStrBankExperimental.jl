```
kernel_mat_sym_bose(ω::T, n::Int, β::T) where {T<:AbstractFloat}
```

対称化されたボソンマツバラ周波数カーネル

$$
\begin{align*}
K_β(\omega, \omega_n) & = \frac{2\omega}{\omega_n^2 + \omega^2},
\end{align*}
$$

ここで、$\omega_n = 2n\pi/\beta$ はボソンに対して $n \in \mathbb{Z}$ です。
