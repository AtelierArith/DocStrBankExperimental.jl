```
diff_conjugate(G::AbstractLieGroup, g, h, X)
diff_conjugate!(G::AbstractLieGroup, Y, g, h, X)
```

[`conjugate`](@ref) $c_g(h) = g∘h∘g^{-1}$ の微分を [`AbstractLieGroup`](@ref) `G` 上で計算します。この操作は `Y` に対してインプレースで実行できます。

$$
  D(c_g(h))[X], \qquad X ∈ \mathfrak g.
$$
