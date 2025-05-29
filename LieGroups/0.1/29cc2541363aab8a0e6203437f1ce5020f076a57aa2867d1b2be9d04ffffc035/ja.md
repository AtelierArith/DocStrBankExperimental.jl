```
diff_left_compose(G::LieGroup{𝔽,AdditionGroupOperation}, g, h, X)
diff_left_compose!(G::LieGroup{𝔽,AdditionGroupOperation}, Y, g, h, X)
```

左群乗法 $λ_g(h) = g∘h$ の微分を計算します。これは [`AdditionGroupOperation`](@ref) に対して簡略化され、$Dλ_g(h)[X] = X$ となります。
