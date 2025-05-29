```
mean(M::Circle{ℂ}, x::AbstractVector[, w::AbstractWeights])
```

複素数で表される点の[`Circle`](@ref) $𝕊^1$上の`x`のリーマン平均[`mean`](@ref mean(M::AbstractManifold, args...))を計算します。合計を計算すると

$$
s = \sum_{i=1}^n x_i
$$

平均は複素数$s$の角度であり、したがって複素平面では$\frac{s}{\lvert s \rvert}$として表されます。ただし、$s \neq 0$のときです。

合計$s=0$の場合、平均は一意ではありません。たとえば、反対の点や等間隔の角度の場合です。
