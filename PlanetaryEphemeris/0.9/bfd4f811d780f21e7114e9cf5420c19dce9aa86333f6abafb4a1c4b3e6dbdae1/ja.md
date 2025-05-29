```
Ry(alpha::T) where {T<:Number}
```

y軸周りの回転行列を返します

$$
R_y(\alpha) =
\left[
\begin{array}{ccc}
    \cos\alpha & 0 & -\sin\alpha \\
    0 & 1 & 0 \\
    \sin\alpha & 0 & \cos\alpha \\
\end{array}
\right],
$$

ここで、$\alpha$はラジアン単位の角度です。

https://ui.adsabs.harvard.edu/abs/2014IPNPR.196C...1F%2F/abstractの9ページの式(12)を参照してください。

$$
\textbf{注意:}
$$

Lieske et al. (1977, 1979)は、この行列が（`Rx`、`Rz`に対して）サイン項の外側で符号が逆であるという慣習を導入しています。https://ui.adsabs.harvard.edu/abs/1977A%26A....58....1L/abstractの3ページの式(4)およびhttps://ui.adsabs.harvard.edu/abs/1979A%26A....73..282L/abstractの283ページの式(3)を参照してください。

また、[`Rx`](@ref)および[`Rz`](@ref)も参照してください。
