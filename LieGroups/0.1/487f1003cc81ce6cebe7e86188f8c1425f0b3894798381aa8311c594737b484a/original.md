```
TranslationGroup{𝔽,T}
```

The translation group $\mathcal T(n)$ is Lie group consisting of the [`AdditionGroupOperation`](@ref) on some [`Euclidean`](@extref `Manifolds.Euclidean`) space.

# Constructor

```
TranslationGroup(n₁,...,nᵢ; kwargs...)
```

Generate the translation group on $𝔽^{n₁,…,nᵢ}$ = `Euclidean(n₁,...,nᵢ; field=𝔽)`, which is isomorphic to the group itself. All keyword arguments in `kwargs...` are passed on to [`Euclidean`](@extref `Manifolds.Euclidean`) as well

We denote the Lie algebra of $\mathcal T(n)$ by $\mathfrak t(n)$.
