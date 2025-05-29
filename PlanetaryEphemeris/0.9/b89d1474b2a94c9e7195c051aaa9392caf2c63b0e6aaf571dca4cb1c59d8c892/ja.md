```
ITM2(ωx::T, ωy::T, ωz::T) where {T <: Number}
```

月の慣性モーメントの時間依存部分の第二項を返します

$$
\frac{k_{2,M} R_M^5}{3G}
\left[
\begin{array}{ccc}
    \omega_{m,x}^2 - \frac{1}{3}(\omega_m^2 - n^2) & \omega_{m,x}\omega_{m,y} & \omega_{m,x}\omega_{m,z} \\
    \omega_{m,x}\omega_{m,y} & \omega_{m,y}^2 - \frac{1}{3}(\omega_m^2 - n^2) & \omega_{m,y}\omega_{m,z} \\
    \omega_{m,x}\omega_{m,z} & \omega_{m,y}\omega_{m,z} & \omega_{m,z}^2 - \frac{1}{3}(\omega_m^2 + 2n^2) \\
\end{array}
\right],
$$

ここで、$\mathbf{\omega}_m = (\omega_{m,x}, \omega_{m,y}, \omega_{m,z})$ はマントルフレームにおけるマントルの角速度、$k_{2,M}$ は月のポテンシャルラブ数、$R_M$ は月の赤道半径、$n$ は月の平均運動です。

$$
\textbf{注意：}
$$

オイラー角は時間 $t-τ_M$ で評価する必要があります。

https://ui.adsabs.harvard.edu/abs/2014IPNPR.196C...1F%2F/abstract の17ページの式(41)の第二項を参照してください。

また、[`ITM1`](@ref) と [`ITM`](@ref) も参照してください。
