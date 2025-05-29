```
indices(x::Stencil, I::Union{Tuple,CartesianIndex})
indices(x::AbstractStencilArray, I::Union{Tuple,CartesianIndex})
```

`I`の周りの各隣接点に対する`CartesianIndices`の`SVector`を返します。

`Stencil`の`indices`は配列の境界を認識せず、ラップや反射は行いません。`AbstractStencilArray`では、配列の境界条件に応じてラップや反射が行われます。
