```
SphericalCap{T} <: ParametricSurface{T}
```

Spherical cap surface, creates a half-space which is essentially the subtraction of a sphere from an infinite plane. Only the spherical cap itself is visualized, not the plane. The positive normal side is outside the surface.

**Can be used as a detector in [`AbstractOpticalSystem`](@ref)s.**

```julia
SphericalCap(radius::T, ϕmax::T, [surfacenormal::SVector{3,T}, centrepoint::SVector{3,T}]; interface::NullOrFresnel{T} = nullinterface(T))
```

The minimal case returns a spherical cap centered at the origin with `surfacenormal = [0, 0, 1]`.
