```
Rz(alpha::T) where {T<:Number}
```

z軸周りの回転行列を返します

$$
R_z(\alpha) =
\left[
\begin{array}{ccc}
    \cos\alpha & \sin\alpha & 0 \\
    -\sin\alpha & \cos\alpha & 0 \\
    0 & 0 & 1 \\
\end{array}
\right],
$$

ここで、$\alpha$はラジアン単位の角度です。

https://ui.adsabs.harvard.edu/abs/2014IPNPR.196C...1F%2F/abstractの9ページの式(13)を参照してください。

また、[`Rx`](@ref)および[`Ry`](@ref)も参照してください。
