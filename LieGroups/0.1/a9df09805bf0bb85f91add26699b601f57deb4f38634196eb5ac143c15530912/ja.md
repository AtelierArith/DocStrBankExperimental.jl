```
diff_right_compose(G::AbstractLieGroup, h, g, X)
diff_right_compose!(G::AbstractLieGroup, Y, h, g, X)
```

右群乗法の微分 $ρ_g(h) = h∘g$ を [`AbstractLieGroup`](@ref) `G` 上で計算します。すなわち、$Dρ_g(h)[X]$ を計算します。ここで、$X ∈ 𝔤$ です。これは `Y` のインプレースで行うことができます。
