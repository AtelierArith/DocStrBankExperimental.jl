```
nearestOrthogonal(X::AnyMatrix)
```

**エイリアス**: `nearestOrth`

平方の `Hermitian`、`LowerTriangular`、`Diagonal` または一般的な `Matrix` `X` の最近接直交行列を返します（[AnyMatrix type](@ref)を参照）。これは次のように与えられます。

$$
UV^H
$$

,

ここで

$$
\textrm(SVD)=UΛV^H
$$

。

もし `X` が `Diagonal` の場合、`X` を返します。

**参照**: [`nearestPosDef`](@ref)、[`procrustes`](@ref)。

**例**

```julia
using PosDefManifold
U=nearestOrth(randn(5, 5))
```
