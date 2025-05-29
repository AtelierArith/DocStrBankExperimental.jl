```
DistanceGradient <: NeutralLandscapeMaker

DistanceGradient(; sources=[1])
DistanceGradient(sources)
```

The `sources` field is a `Vector{Integer}` of *linear* indices of the matrix,  from which the distance must be calculated.
