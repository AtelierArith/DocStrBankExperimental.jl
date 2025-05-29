```
TranslationGroup{T,𝔽} <: GroupManifold{Euclidean{T,𝔽},AdditionOperation,LeftInvariantRepresentation}
```

Translation group $\mathrm{T}(n)$ represented by translation arrays.

# Constructor

```
TranslationGroup(n₁,...,nᵢ; field=𝔽, parameter::Symbol=:type)
```

Generate the translation group on $𝔽^{n₁,…,nᵢ}$ = `Euclidean(n₁,...,nᵢ; field=𝔽)`, which is isomorphic to the group itself.
