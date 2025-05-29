```
change_representer(::SymplecticMatrices, ::EuclideanMetric, p, X)
change_representer!(::SymplecticMatrices, Y, ::EuclideanMetric, p, X)
```

Compute the representation of a tangent vector $ξ ∈ T_p\mathrm{Sp}(2n, ℝ)$ s.t.

$$
  g_p(c_p(ξ), η) = ⟨ξ, η⟩^{\text{Euc}} \text{for all } η ∈ T_p\mathrm{Sp}(2n, ℝ).
$$

with the conversion function

$$
  c_p : T_p\mathrm{Sp}(2n, ℝ) → T_p\mathrm{Sp}(2n, ℝ), \quad
  c_p(ξ) = \frac{1}{2} pp^{\mathrm{T}} ξ + \frac{1}{2} pJ_{2n} ξ^{\mathrm{T}} pJ_{2n},
$$

where $J_{2n} = \begin{bmatrix} 0_n & I_n \\ -I_n & 0_n \end{bmatrix}$ denotes the [`SymplecticElement`](@ref).

Each of the terms $c_p^1(ξ) = p p^{\mathrm{T}} ξ$ and $c_p^2(ξ) = pJ_{2n} ξ^{\mathrm{T}} pJ_{2n}$ from the above definition of $c_p(η)$ are themselves metric compatible in the sense that

$$
    c_p^i : T_p\mathrm{Sp}(2n, ℝ) → ℝ^{2n×2n}\quad
    g_p^i(c_p(ξ), η) = ⟨ξ, η⟩^{\text{Euc}} \;∀\; η ∈ T_p\mathrm{Sp}(2n, ℝ),
$$

for $i \in {1, 2}$. However the range of each function alone is not confined to   $T_p\mathrm{Sp}(2n, ℝ)$, but the convex combination

$$
    c_p(ξ) = \frac{1}{2}c_p^1(ξ) + \frac{1}{2}c_p^2(ξ)
$$

does have the correct range $T_p\mathrm{Sp}(2n, ℝ)$.
