```
diff_inv(G::LieGroup{ℝ, AdditionGroupOperation, Circle{ℝ}}, g, X)
diff_inv!(G::LieGroup{ℝ, AdditionGroupOperation, Circle{ℝ}}, Y, g, X)
```

逆写像 $Dι_{\mathcal G}([g])[X]$ を計算します。ここで、逆写像は $ι_{\mathcal G}([g]) := [g]^{-1} = [-g]$ であり、$X ∈ 𝔤$ は [Lie代数](@ref) $𝔤$ の元で、[実 `CircleGroup`](@ref circle-group-real) `G` は $=\mathcal G$ です。

計算は可換性により簡略化され、

$$
Dι_{\mathcal G}([g])[X] = -X.
$$

`Y` が `mutable` であれば、これを `Y` のインプレースで計算できます。
