```
inv_right_compose(G::AbstractLieGroup, h, g)
inv_right_compose!(G::AbstractLieGroup, k, h, g)
```

右群演算の逆を計算します $ρ_g(h) = h∘g$、[`AbstractLieGroup`](@ref) `G` 上で、すなわち $ρ_g^{-1}(h) = h∘g^{-1}$ を計算します。これは `k` のインプレースで行うことができます。
