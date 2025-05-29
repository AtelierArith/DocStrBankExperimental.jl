```
diff_right_compose(G::LieGroup{𝔽,<:AbstractMultiplicationGroupOperation}, h, g, X)
diff_right_compose!(G::LieGroup{𝔽,<:AbstractMultiplicationGroupOperation}, Y, h, g, X)
```

右群乗法の微分を計算します $ρ_g(h) = h∘g$。これは[`AbstractMultiplicationGroupOperation`](@ref)の場合、$Dρ_g(h)[X] = Xg$に簡略化されます。
