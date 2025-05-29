```
Mixed(; left = nothing, right = nothing, bottom = nothing, top = nothing)
```

Construct a `Mixed` AlignMode, which has different behavior on each side. Arguments that are `nothing` will exclude protrusions from the bounding box on that side. Those that are real numbers will be padded by that amount and include protrusions from the bounding box on that side. Arguments that are `Protrusion` will override the protrusion with a fixed value.
