```
diff_conjugate(G::LieGroup{𝔽,AdditionGroupOperation}, g, h, X)
diff_conjugate!(G::LieGroup{𝔽,AdditionGroupOperation}, Y, g, h, X)
```

共役の微分を計算します $c_g(h) = g∘h∘g^{-1} = g+h-g = h$。これは [`AdditionGroupOperation`](@ref) に対して簡略化され、$D(c_g(h))[X] = X$ となります。
