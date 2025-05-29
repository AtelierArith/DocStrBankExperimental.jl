```
Rx(alpha::T) where {T<:Number}
```

x軸周りの回転行列を返します

$$
R_x(\alpha) =
\left[
\begin{array}{ccc}
    1 & 0 & 0 \\
    0 & \cos\alpha & \sin\alpha \\
    0 & -\sin\alpha & \cos\alpha \\
\end{array}
\right],
$$

ここで、$\alpha$はラジアン単位の角度です。

https://ui.adsabs.harvard.edu/abs/2014IPNPR.196C...1F%2F/abstractの9ページの式(11)を参照してください。

また、[`Ry`](@ref)および[`Rz`](@ref)も参照してください。
