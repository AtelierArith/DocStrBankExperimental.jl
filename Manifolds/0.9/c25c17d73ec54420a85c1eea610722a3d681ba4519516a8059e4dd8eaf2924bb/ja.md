```
project(M::SkewHermitianMatrices, p)
```

`p`を埋め込みから[`SkewHermitianMatrices`](@ref) `M`に射影します。すなわち、

$$
\operatorname{proj}_{\operatorname{SkewHerm}(n)}(p) = \frac{1}{2} \bigl( p - p^{\mathrm{H}} \bigr),
$$

ここで、$⋅^{\mathrm{H}}$はエルミート、すなわち複素共役転置を示します。
