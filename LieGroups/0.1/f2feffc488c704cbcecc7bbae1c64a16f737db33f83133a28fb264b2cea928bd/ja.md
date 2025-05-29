```
diff_conjugate(G::LieGroup{ℝ, AdditionGroupOperation, Circle{ℝ}}, g, h, X)
diff_conjugate!(G::LieGroup{ℝ, AdditionGroupOperation, Circle{ℝ}}, Y, g, h, X)
```

[共役写像](@ref conjugate) $c_g(h) = g∘h∘g^{-1}=h$ の微分を計算します。実数直線の[一部として表される](@ref circle-group-real)円群では、これは $D(c_g(h))[X] = X$ に簡略化されます。

`Y` が `mutable` であれば、`Y` のインプレースで計算できます。
