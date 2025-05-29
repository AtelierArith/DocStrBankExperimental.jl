```
knots(basis::BSplineBasis)
```

Bスプライン基底のノット列を返します。

ノット列はブレークポイント列ですが、最初と最後の値が重複しており、`order(basis)` 回表示されます。

# 例

```jldoctest
julia> knots(BSplineBasis(3, 0:5))
10-element BSplines.KnotVector{Int64, UnitRange{Int64}}:
 0
 0
 0
 1
 2
 3
 4
 5
 5
 5
```
