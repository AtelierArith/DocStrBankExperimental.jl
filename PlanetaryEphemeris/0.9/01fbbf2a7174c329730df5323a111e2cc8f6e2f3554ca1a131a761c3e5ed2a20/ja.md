```
ITM1(x::T, y::T, z::T) where {T <: Number}
```

月の慣性モーメントの時間依存部分の最初の項を返します

$$
-\frac{k_{2,M} m_E R_M^5}{r^5}
\left[
\begin{array}{ccc}
    x^2 - \frac{1}{3}r^2 & xy & xz \\
    xy & y^2 - \frac{1}{3}r^2 & yz \\
    xz & yz & z^2 - \frac{1}{3}r^2 \\
\end{array}
\right],
$$

ここで、$\mathbf{r} = (x, y, z)$は地球に対する月の位置をマントルフレームで表したものであり、$k_{2,M}$は月のポテンシャルラブ数、$m_E$は地球の質量、$R_M$は月の赤道半径です。

https://ui.adsabs.harvard.edu/abs/2014IPNPR.196C...1F%2F/abstractの17ページの式(41)の最初の項を参照してください。

また、[`ITM2`](@ref)および[`ITM`](@ref)も参照してください。
