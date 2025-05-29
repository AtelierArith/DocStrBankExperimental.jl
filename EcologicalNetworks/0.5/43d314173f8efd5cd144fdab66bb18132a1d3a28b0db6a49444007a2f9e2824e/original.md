```
trophic_level(N::UnipartiteNetwork; kwargs...)
```

Returns the *fractional* trophic level (after Odum & Heald 1975) of species in a binary unipartite network. The trophic level is calculated after Pauly & Christensen (1995), specifically as TLᵢ = 1 + ∑ⱼ(TLⱼ×DCᵢⱼ)/∑ⱼ(DCᵢⱼ), wherein TLᵢ is the trophic level of species i, and DCᵢⱼ is the proportion of species j in the diet of species i. Note that this function is calculated on a network where the diagonal (i.e. self loops) are removed.

This function uses a *pseudo*-inverse to solve the linear system described above *iff* the determinant of the diet matrix is 0 (it is non-invertible). Otherwise, it will use an exact inverse.
