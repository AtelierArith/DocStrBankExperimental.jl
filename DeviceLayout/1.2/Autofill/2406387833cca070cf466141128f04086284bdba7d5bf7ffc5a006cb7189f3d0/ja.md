```
autofill!(cs::AbstractCoordinateSystem,
    filler_cs::AbstractCoordinateSystem,
    grid_x::AbstractArray,
    grid_y::AbstractArray,
    exclusion)
```

`cs`内の`filler_cs`への参照を、`exclusion`ポリゴンに含まれないグリッドポイントで追加します。

`exclusion`引数は以下のいずれかである可能性があります。

  * `cs`内の形状から除外された領域を生成するために使用されるオフセットを示す`Coordinate`
  * 除外された領域の幾何学を含む`CoordinateSystem`または`Cell`
  * `cs`から`CoordinateSystem`または`Cell`を作成する`Function`
  * `AbstractArray{<:AbstractPolygon}`

参照の起点を返します。
