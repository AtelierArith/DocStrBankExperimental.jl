```
diff_conjugate(G::LieGroup{𝔽,<:AbstractMultiplicationGroupOperation}, g, h, X)
diff_conjugate!(G::LieGroup{𝔽,<:AbstractMultiplicationGroupOperation}, Y, g, h, X)
```

共役の微分を計算します $c_g(h) = g∘h∘g^{-1} = ghg^{-1}$。これは [`AbstractMultiplicationGroupOperation`](@ref) に対して簡略化され、$D(c_g(h))[X] = gXg^{-1}$ となります。
