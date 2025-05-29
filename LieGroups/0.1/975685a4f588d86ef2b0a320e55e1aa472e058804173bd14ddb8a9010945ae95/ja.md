```
diff_left_compose(G::AbstractLieGroup, g, h, X)
diff_left_compose!(G::AbstractLieGroup, Y, g, h, X)
```

左群乗法 $λ_g(h) = g∘h$ の微分を計算します。これは [`AbstractLieGroup`](@ref) `G` 上で行われ、$Dλ_g(h)[X]$ を計算します。ここで、$X ∈ 𝔤$ です。これは `Y` のインプレースで行うことができます。
