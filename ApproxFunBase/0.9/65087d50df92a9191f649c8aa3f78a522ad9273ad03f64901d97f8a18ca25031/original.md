```
Conversion_normalizedspace(S::Space, direction::Val{:forward} = Val(:forward))
```

Return `Conversion(S, normalizedspace(S))`. This may be concretely inferred for orthogonal polynomial spaces.

```
Conversion_normalizedspace(S::Space, ::Val{:backward})
```

Return `Conversion(normalizedspace(S), S)`. This may be concretely inferred for orthogonal polynomial spaces.
