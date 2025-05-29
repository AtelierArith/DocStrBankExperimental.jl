```
sref(x::GeometryStructure{T}, origin=zero(Point{T}); kwargs...)
```

Convenience constructor for `StructureReference{float(T), typeof(x)}`.

Synonyms are accepted for these keywords:

```
- X-reflection: `:xrefl`, `:xreflection`, `:refl`, `:reflect`, `:xreflect`,
`:xmirror`, `:mirror`
- Magnification: `:mag`, `:magnification`, `:magnify`, `:zoom`, `:scale`
- Rotation: `:rot`, `:rotation`, `:rotate`, `:angle`
```
