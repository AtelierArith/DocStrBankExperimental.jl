```
diff_conjugate(G::LieGroup{𝔽,<:AbelianMultiplicationGroupOperation}, g, h, X)
diff_conjugate!(G::LieGroup{𝔽,<:AbelianMultiplicationGroupOperation}, Y, g, h, X)
```

共役の微分を計算します $c_g(h) = g∘h∘g^{-1} = ghg^{-1}$。これは [`AbelianMultiplicationGroupOperation`](@ref) の場合、$D(c_g(h))[X] = X$ に簡略化されます。

`Y` が `mutable` であれば、`Y` のインプレースで計算できます。
