```
diff_inv(G::LieGroup{𝔽,<:AbelianMultiplicationGroupOperation}, g, X)
diff_inv!(G::LieGroup{𝔽,<:AbelianMultiplicationGroupOperation}, Y, g, X)
```

逆元 $ι_{\mathcal G}(g) := g^{-1}$ の微分 $Dι_{\mathcal G}(g)[X]$ を、[`LieGroup`](@ref) `G` の [`LieAlgebra`](@ref) $𝔤$ における $X ∈ 𝔤$ で計算します。

アーベルの場合、計算は次のように簡略化されます。

$$
Dι_{\mathcal G}(g)[X] = -gXg^{-1} = -X.
$$

`Y` が `mutable` であれば、これを `Y` のインプレースで計算できます。
