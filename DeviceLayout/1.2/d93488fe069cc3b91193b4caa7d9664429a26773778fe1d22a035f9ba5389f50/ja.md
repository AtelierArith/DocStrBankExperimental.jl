```
StructureReference(x::GeometryStructure{S}; kwargs...) where {S <: Coordinate}
StructureReference(x::GeometryStructure{S}, origin::Point{T}; kwargs...) where
    {S <: Coordinate, T <: Coordinate}
StructureReference(x, origin::Point{T}; kwargs...) where {T <: Coordinate}
```

`StructureReference{float(T), typeof(x)}`の便利なコンストラクタです。

キーワード引数はx反射、拡大、または回転を指定できます。 "正しいキーワード"を忘れた場合に備えて、同義語が受け入れられます...

  * X反射: `:xrefl`, `:xreflection`, `:refl`, `:reflect`, `:xreflect`, `:xmirror`, `:mirror`
  * 拡大: `:mag`, `:magnification`, `:magnify`, `:zoom`, `:scale`
  * 回転: `:rot`, `:rotation`, `:rotate`, `:angle`
