```
subduction_count(Dᴳᵢ, Dᴴⱼ[, αβγᴴⱼ]) --> Int
```

For two groups $G$ and $H$, where $H$ is a subgroup of $G$, i.e. $H<G$, with associated irreducible representations `Dᴳᵢ` = $D^G_i(g)$ and `Dᴴⱼ` = $D^H_j(g)$ over operations $g∈G$ and $h∈H<G$, compute the compatibility relation between the two irreps from the subduction reduction formula (or "magic" formula/Schur orthogonality relation), returning how many times $n^{GH}_{ij}$ the subduced representation $D^G_i↓H$ contains  the irrep $D^H_j$; in other words, this gives the compatibility between the two irreps.

Optionally, a vector `αβγᴴⱼ` may be provided, to evaluate the characters/irreps  of `Dᴳᵢ` at a concrete value of $(α,β,γ)$. This is e.g. meaningful for `LGIrrep`s at non-special **k**-vectors. Defaults to `nothing`.

The result is computed using the reduction formula [see e.g. Eq. (15) of [arXiv:1706.09272v2](https://arxiv.org/abs/1706.09272)]:

$n^{GH}_{ij} = |H|^{-1} \sum_h \chi^G_i(h)\chi^H_j(h)^*$

## Example

Consider the two compatible **k**-vectors Γ (a point) and Σ (a line) in space group 207:

```jl
lgirsd  = lgirreps(207, Val(3));
Γ_lgirs = lgirsd["Γ"]; # at Γ ≡ [0.0, 0.0, 0.0]
Σ_lgirs = lgirsd["Σ"]; # at Σ ≡ [α, α, 0.0]
```

We can test their compatibility via:

```jl
[[subduction_count(Γi, Σj) for Γi in Γ_lgirs] for Σj in Σ_lgirs]
> # Γ₁ Γ₂ Γ₃ Γ₄ Γ₅
>  [ 1, 0, 1, 1, 2] # Σ₁
>  [ 0, 1, 1, 2, 1] # Σ₂
```

With following enterpretatation for compatibility relations between irreps at Γ and Σ:

| Compatibility relation | Degeneracies |
| ----------------------:| ------------:|
|                Γ₁ → Σ₁ |        1 → 1 |
|                Γ₂ → Σ₂ |        1 → 1 |
|           Γ₃ → Σ₁ + Σ₂ |    2 → 1 + 1 |
|          Γ₄ → Σ₁ + 2Σ₂ |    3 → 1 + 2 |
|          Γ₅ → 2Σ₁ + Σ₂ |    3 → 2 + 1 |

where, in this case, all the small irreps are one-dimensional.
