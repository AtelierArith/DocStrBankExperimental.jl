```
StructureReference(x::GeometryStructure{S}; kwargs...) where {S <: Coordinate}
StructureReference(x::GeometryStructure{S}, origin::Point{T}; kwargs...) where
    {S <: Coordinate, T <: Coordinate}
StructureReference(x, origin::Point{T}; kwargs...) where {T <: Coordinate}
```

Convenience constructor for `StructureReference{float(T), typeof(x)}`.

Keyword arguments can specify x-reflection, magnification, or rotation. Synonyms are accepted, in case you forget the "correct keyword"...

  * X-reflection: `:xrefl`, `:xreflection`, `:refl`, `:reflect`, `:xreflect`, `:xmirror`, `:mirror`
  * Magnification: `:mag`, `:magnification`, `:magnify`, `:zoom`, `:scale`
  * Rotation: `:rot`, `:rotation`, `:rotate`, `:angle`
