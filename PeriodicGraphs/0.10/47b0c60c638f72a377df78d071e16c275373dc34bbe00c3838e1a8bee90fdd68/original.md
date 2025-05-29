```
RingAttributions(g::PeriodicGraph{D}, [strong::Bool=false,] [depth::Integer=15,] symmetries::AbstractSymmetryGroup=NoSymmetryGroup(g), dist::DistanceRecord=DistanceRecord(g,depth)) where D
```

Return the rings of `g` sorted into a `RingAttributions`.

If `strong` is set, only the strong rings are kept. See [`rings`](@ref) for the meaning of the other arguments.
