It is possible to create the subset of any `AbstractUnitRangesSortedSet`, like a `view` for `Array`s:

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

The `subset` object is an static, iterable view of the container

```
struct UnitRangesSortedSubSet{K, TU, P, Tix} <: AbstractUnitRangesSortedSubSet{K, TU, P}
```
