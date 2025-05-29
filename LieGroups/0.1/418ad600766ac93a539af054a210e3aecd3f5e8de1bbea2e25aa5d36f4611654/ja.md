```
diff_right_compose(G::LieGroup{𝔽,AdditionGroupOperation}, h, g, X)
diff_right_compose!(G::LieGroup{𝔽,AdditionGroupOperation}, Y, h, g, X)
```

右群乗法の微分を計算します $ρ_g(h) = h∘g$。これは [`AdditionGroupOperation`](@ref) に対して簡略化され、$Dρ_g(h)[X] = X$ となります。
