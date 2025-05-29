```
nearestOrthogonal(X::AnyMatrix)
```

**alias**: `nearestOrth`

Return the nearest orthogonal matrix  of a square `Hermitian`, `LowerTriangular`, `Diagonal` or generic `Matrix` `X`  (see [AnyMatrix type](@ref)).  This is given by

$UV^H$,

where

$\textrm(SVD)=UΛV^H$.

If `X` is `Diagonal`, return `X`.

**See also**: [`nearestPosDef`](@ref), [`procrustes`](@ref).

**Examples**

```julia
using PosDefManifold
U=nearestOrth(randn(5, 5))
```
