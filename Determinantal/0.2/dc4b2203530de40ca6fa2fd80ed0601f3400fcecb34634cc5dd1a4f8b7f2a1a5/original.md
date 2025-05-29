```
EllEnsemble(L :: AbstractMatrix{T})
```

Construct an L-ensemble from a (symmetric, non-negative definite) matrix L.

```@example
Z = randn(5, 2)
EllEnsemble(Z * Z') #not very useful, presumably
```

Note that eigen(L) will be called at construction, which may be computationally costly.

An L-Ensemble can also be constructed based on lazy matrix types, i.e. types that leverage a low-rank representation. In the example above we could also use the LowRank type:

```@example
Z = randn(5, 2)
EllEnsemble(LowRank(Z)) #more efficient than Z*Z'
```
