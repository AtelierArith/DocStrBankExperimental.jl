```
newtonpolygon(p::AbstractPolynomial; lowerhull=false)
```

多項式 `p` のサポートから [`NewtonPolygon`](@ref) を構築します。`lowerhull` は、ニュートン多角形の正則分割を構築するために下部または上部の凸包を使用するかどうかを示します。
