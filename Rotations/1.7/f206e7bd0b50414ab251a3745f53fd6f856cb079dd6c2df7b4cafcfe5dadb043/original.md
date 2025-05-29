```
MRP{T} <: Rotation
```

Modified Rodrigues Parameter. Is a 3D parameterization of attitude, and is a sterographic projection of the 4D unit sphere onto the plane tangent to the negative real pole. They have a singularity at θ = ±360°.

# Constructors

MRP(x, y, z) MRP(r::AbstractVector)
