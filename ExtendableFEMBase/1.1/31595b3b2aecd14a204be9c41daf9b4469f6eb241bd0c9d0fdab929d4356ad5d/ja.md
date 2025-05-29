```julia
abstract type QuadratureRule{T<:Real, ET<:ExtendableGrids.AbstractElementGeometry}
```

特定のNumberTypeおよび要素幾何学のための数値積分ルールの抽象型
