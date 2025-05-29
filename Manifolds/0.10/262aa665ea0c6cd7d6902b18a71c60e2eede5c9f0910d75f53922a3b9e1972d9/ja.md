```
change_representer(M::Hyperbolic, ::EuclideanMetric, p::PoincareBallPoint, X::PoincareBallTangentVector)
```

メトリックには各要素に対して $α = \frac{2}{1-\sum_{i=1}^n p_i^2}$ という項があるため、勾配の補正は $Y = \frac{1}{α^2}X$ となります。
