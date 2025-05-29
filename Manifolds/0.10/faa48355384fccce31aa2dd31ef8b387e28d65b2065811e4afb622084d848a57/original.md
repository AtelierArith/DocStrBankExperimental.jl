```
change_representer(MetMan::MetricManifold{<:Any, <:Euclidean, ExtendedSymplecticMetric},
                   EucMet::EuclideanMetric, p, X)
change_representer!(MetMan::MetricManifold{<:Any, <:Euclidean, ExtendedSymplecticMetric},
                    Y, EucMet::EuclideanMetric, p, X)
```

Change the representation of a matrix $ξ ∈ ℝ^{2n×2n}$ into the inner product space $(ℝ^{2n×2n}, g_p)$ where the inner product is given by $g_p(ξ, η) = \langle p^{-1}ξ, p^{-1}η \rangle = \operatorname{tr}(ξ^{\mathrm{T}}(pp^{\mathrm{T}})^{-1}η)$, as the extension of the [`RealSymplecticMetric`](@ref) onto the entire embedding space.

By changing the representation we mean to apply a mapping

$$
    c_p : ℝ^{2n×2n} → ℝ^{2n×2n},
$$

defined by requiring that it satisfy the metric compatibility condition

$$
    g_p(c_p(ξ), η) = ⟨p^{-1}c_p(ξ), p^{-1}η⟩ = ⟨ξ, η⟩^{\text{Euc}}
        \;∀\; η ∈ T_p\mathrm{Sp}(2n, ℝ).
$$

In this case, we compute the mapping

$$
    c_p(ξ) = pp^{\mathrm{T}} ξ.
$$
