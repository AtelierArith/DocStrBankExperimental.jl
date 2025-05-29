```
addarr!(
    c1::AbstractCoordinateSystem,
    c2::GeometryStructure,
    c::AbstractRange,
    r::AbstractRange;
    kwargs...
)
```

Add an `ArrayReference` to `c2` to the list of references in `c1`, based on ranges.

`c` specifies column coordinates and `r` for the rows. Pairs from `c` and `r` specify the origins of the repeated cells. The extrema of the ranges therefore do not specify the extrema of the resulting `ArrayReference`'s bounding box; some care is required.

Keyword arguments specify x-reflection, magnification factor, and rotation, with synonyms allowed:

  * X-reflection: `:xrefl`, `:xreflection`, `:refl`, `:reflect`, `:xreflect`, `:xmirror`, `:mirror`
  * Magnification: `:mag`, `:magnification`, `:magnify`, `:zoom`, `:scale`
  * Rotation: `:rot`, `:rotation`, `:rotate`, `:angle`
