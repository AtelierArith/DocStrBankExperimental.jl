```
diff_inv(G::LieGroup{𝔽,<:AbstractMultiplicationGroupOperation}, g, X)
diff_inv!(G::LieGroup{𝔽,<:AbstractMultiplicationGroupOperation}, Y, g, X)
```

行列の逆数 $ι_{\mathcal G}(g) := g^{-1}$ の微分 $Dι_{\mathcal G}(g)[X]$ を、[`LieAlgebra`](@ref) $𝔤$ の $X ∈ 𝔤$ における [`LieGroup`](@ref) `G` で計算します。

公式は次のようになります。

$$
Dι_{\mathcal G}(g)[X] = -g^{\mathrm{T}}Xg^{-1},
$$

これは、[Giles:2008](@cite) からの逆数の微分 $D(g^{-1})[X] = -g^{-1}Xg^{-1}$ を使用し、左の合成のプッシュフォワード $Dλ_\mathrm{e}(g)[X] = gX$ がリー代数から $g$ における接空間への写像であり、その随伴 $D^*λ_\mathrm{e}(g)[X] = g^{\mathrm{T}}X$ を合成することから導かれます。次に、$g^{\mathrm{T}}(g^{-1}(gX)g^{-1})$ を得て、上記から $-g^{\mathrm{T}}Xg^{-1}$ に簡略化されます。 ```
