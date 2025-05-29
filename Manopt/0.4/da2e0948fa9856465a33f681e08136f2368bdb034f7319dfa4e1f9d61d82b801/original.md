```
NelderMead(M::AbstractManifold, f [, population::NelderMeadSimplex])
```

Solve a Nelder Mead minimization problem for the cost function `f` on the manifold `M`. If the initial population `population` is not given, a random set of points is chosen. If it is given, the computation is done in place of `population`.

For more options see [`NelderMead`](@ref).
