```
gridpoints_in_polygon(poly::AbstractArray{<:AbstractPolygon},
    dx::Coordinate, dy::Coordinate; b=nothing)
```

`poly`内のグリッドポイントに対して`true`を返す`BitArray`を`b`のグリッドポイントに対して返します。

`b`のバウンディングボックス内のグリッドポイントのみが考慮されます。`b`が`nothing`の場合、`bounds(poly)`が使用されます。`dx`と`dy`は、長方形グリッド上の隣接ポイント間の距離です。`BitArray`で表されるグリッドポイントは、`p0 = (m*dx, n*dy)`という左下のポイントから始まり、`m`と`n`は整数で、`p0`は`b`内にあります。

すべてのポリゴンは同じ向き（時計回りまたは反時計回り）である必要があります。混合（例えば「穴」を表すために）は、ポリゴンまたは穴のエッジで望ましい動作をしない可能性があります。
