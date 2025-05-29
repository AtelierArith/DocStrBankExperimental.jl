```
StiefelManifold <: Manifold
```

An implementation of the Stiefel manifold [hairer2006geometric](@cite). The Stiefel manifold is the collection of all matrices $Y\in\mathbb{R}^{N\times{}n}$ whose columns are orthonormal, i.e. 

$$
    St(n, N) = \{Y: Y^TY = \mathbb{I}_n \}.
$$

The Stiefel manifold can be shown to have manifold structure (as the name suggests) and this is heavily used in `GeometricMachineLearning`. It is further a compact space.  More information can be found in the docstrings for [`rgrad(::StiefelManifold, ::AbstractMatrix)`](@ref) and [`metric(::StiefelManifold, ::AbstractMatrix, ::AbstractMatrix)`](@ref).
