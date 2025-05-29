```
inv_left_compose(G::AbstractLieGroup, g, h)
inv_left_compose!(G::AbstractLieGroup, k, g, h)
```

左群演算の逆を計算します $λ_g(h) = g∘h$、[`AbstractLieGroup`](@ref) `G` 上で、すなわち $λ_g^{-1}(h) = g^{-1}∘h$ を計算します。これは `k` のインプレースで行うことができます。
