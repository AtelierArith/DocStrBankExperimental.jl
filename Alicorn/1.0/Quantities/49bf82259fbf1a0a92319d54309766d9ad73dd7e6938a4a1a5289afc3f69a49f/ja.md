```
SimpleQuantity(quantity::AbstractQuantity)
```

任意の `AbstractQuantity` の実装から `SimpleQuantity` を構築します。

`quantity` が `SimpleQuantity` 型の場合は、そのまま返されます。`quantity` が `Quantity` 型の場合は、`quantity.InternalUnits` で指定された SI 単位で表現されます。

# 例

```jldoctest
julia> ucat = UnitCatalogue() ; intu = InternalUnits(length=2*ucat.milli*ucat.meter) ;

julia> q = Quantity(4, Dimension(L=1), intu)
Quantity{Int64} of dimension L^1 in units of (2 mm):
 4
julia> sq = SimpleQuantity(q)
8 mm
```
