```
addref!(c1::AbstractCoordinateSystem{T},
    c2::GeometryStructure,
    origin=zero(Point{T});
    kwargs...)
```

Add a reference to `c2` to the list of references in `c1`.

The reference to `c2` has origin `origin`; x-reflection, magnification factor, and rotation are set by keywords arguments.

Synonyms are accepted for these keywords:

  * X-reflection: `:xrefl`, `:xreflection`, `:refl`, `:reflect`, `:xreflect`, `:xmirror`, `:mirror`
  * Magnification: `:mag`, `:magnification`, `:magnify`, `:zoom`, `:scale`
  * Rotation: `:rot`, `:rotation`, `:rotate`, `:angle`
