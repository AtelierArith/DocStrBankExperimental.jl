```
diff_left_compose(G::LieGroup{𝔽,<:AbstractMultiplicationGroupOperation}, g, h, X)
diff_left_compose!(G::LieGroup{𝔽,<:AbstractMultiplicationGroupOperation}, Y, g, h, X)
```

左群乗法の微分を計算します $λ_g(h) = g∘h$。これは [`AbstractMultiplicationGroupOperation`](@ref) に対して簡略化され、$Dλ_g(h)[X] = gX$ となります。
