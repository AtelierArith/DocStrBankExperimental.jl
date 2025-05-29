```julia
inducevelocity(
    s::StaticArraysCore.SVector{2, AbstractArray},
    xeval
) -> Any

```

Computes the induced velocity by one segment `s` of a unit-strength vortex filament on the evaluation point `xeval`. In case both vertices of the segment have an infinite coordinate (which have to be in the same direction), then the non-infinite coordinates are averaged over the two vertices to calculate the distance from xeval to the segment.
