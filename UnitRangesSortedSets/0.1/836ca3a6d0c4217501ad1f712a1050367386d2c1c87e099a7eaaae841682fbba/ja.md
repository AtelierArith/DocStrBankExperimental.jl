任意の `AbstractUnitRangesSortedSet` のサブセットを作成することが可能であり、これは `Array` の `view` のように機能します：

```julia
julia> urs = UnitRangesSortedSet((1:2, 10:12))
UnitRangesSortedSet{Int64} with 2 elements:
   1:2
  10:12

julia> ss = subset(urs, 0:10)
2-element subset(UnitRangesSortedSet{Int64}, DataStructures.Tokens.IntSemiToken(3):DataStructures.Tokens.IntSemiToken(4)):
   1:2
  10:10
```

`subset` オブジェクトは、コンテナの静的で反復可能なビューです。

```
struct UnitRangesSortedSubSet{K, TU, P, Tix} <: AbstractUnitRangesSortedSubSet{K, TU, P}
```
