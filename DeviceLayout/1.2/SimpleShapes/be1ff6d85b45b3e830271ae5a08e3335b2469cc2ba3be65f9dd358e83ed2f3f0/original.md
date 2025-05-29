```
interdigit!(c::AbstractCoordinateSystem{T}, width, length, fingergap, fingeroffset, npairs::Integer,
    skiplast, meta::Meta=GDSMeta(0,0)) where {T}
```

Creates interdigitated fingers, e.g. for a lumped element capacitor.

  * `width`: finger width
  * `length`: finger length
  * `fingeroffset`: x-offset at ends of fingers
  * `fingergap`: gap between fingers
  * `npairs`: number of fingers
  * `skiplast`: should we skip the last finger, leaving an odd number?
