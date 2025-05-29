```
CoupledVariable(node::Asap.AbstractNode, ref::SpatialVariable, factor::Union{Float64, Vector{Float64}} = 1.0)
```

`node`のための`SpatialVariable`を作成し、`ref.value`に`factor` * `ref.vec`の方向で結合します。

`factor`はスカラーまたはR³のベクトルです。
