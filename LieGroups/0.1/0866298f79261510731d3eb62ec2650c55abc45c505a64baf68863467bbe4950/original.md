```
SpecialLinear{𝔽,T}
```

The special linear group $\mathrm{SL}(n,𝔽)$ is the group of all invertible matrices with unit determinant in $𝔽^{n×n}$ and the [`MatrixMultiplicationGroupOperation`](@ref) as group operation.

The Lie algebra $\mathfrak sl(n, 𝔽) = T_e \mathrm{SL}(n,𝔽)$ is the set of all matrices in $𝔽^{n×n}$ with trace of zero. By default, tangent vectors $X_p ∈ T_p \mathrm{SL}(n,𝔽)$ for $p ∈ \mathrm{SL}(n,𝔽)$ are represented with their corresponding Lie algebra vector $X_e = p^{-1}X_p ∈ 𝔰𝔩(n, 𝔽)$.

# Constructor

```
GeneralLinearGroup(n::Int, field=ℝ; kwargs...)
```

Generate the general linear group  group on $𝔽^{n×n}$. All keyword arguments in `kwargs...` are passed on to [`DeterminantOneMatrices`](@extref `Manifolds.DeterminantOneMatrices`).
