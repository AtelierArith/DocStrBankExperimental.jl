```
change_representer(MetMan::MetricManifold{<:Any, <:Euclidean, ExtendedSymplecticMetric},
                   EucMet::EuclideanMetric, p, X)
change_representer!(MetMan::MetricManifold{<:Any, <:Euclidean, ExtendedSymplecticMetric},
                    Y, EucMet::EuclideanMetric, p, X)
```

行列 $ξ ∈ ℝ^{2n×2n}$ の表現を内積空間 $(ℝ^{2n×2n}, g_p)$ に変換します。ここで、内積は $g_p(ξ, η) = \langle p^{-1}ξ, p^{-1}η \rangle = \operatorname{tr}(ξ^{\mathrm{T}}(pp^{\mathrm{T}})^{-1}η)$ によって与えられ、[`RealSymplecticMetric`](@ref) の全埋め込み空間への拡張として定義されます。

表現を変更するとは、次のマッピングを適用することを意味します。

$$
    c_p : ℝ^{2n×2n} → ℝ^{2n×2n},
$$

これは、メトリックの互換性条件を満たすことを要求することによって定義されます。

$$
    g_p(c_p(ξ), η) = ⟨p^{-1}c_p(ξ), p^{-1}η⟩ = ⟨ξ, η⟩^{\text{Euc}}
        \;∀\; η ∈ T_p\mathrm{Sp}(2n, ℝ).
$$

この場合、マッピングを計算します。

$$
    c_p(ξ) = pp^{\mathrm{T}} ξ.
$$
