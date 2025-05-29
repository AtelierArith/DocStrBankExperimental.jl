```
adjoint(G::AbstractLieGroup, g, X)
adjoint!(G::AbstractLieGroup, Y, g, X)
```

隣接作用素 $\mathrm{Ad}(g): \mathfrak g → \mathfrak g$ を計算します。これは、[`conjugate`](@ref) $c_g(h) = g∘h∘g^{-1}$ の微分 [`diff_conjugate`](@ref) として定義され、[`Identity`](@ref) $h=\mathrm{e}$ で評価されます。この操作は `Y` のインプレースで実行できます。

$$
  \mathrm{Ad}(g)[X] = D c_g(\mathrm{e}) [X], \qquad X ∈ \mathfrak g.
$$

詳細は [HilgertNeeb:2012; Section 9.2.3](@cite) を参照してください。

行列リー群では、隣接作用素は $\mathrm{Ad}(g)[X] = g∘X∘g^{-1}$ となります。 ```
