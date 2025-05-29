```
Rectangle{T} <: Surface{T}
```

Rectangular surface, not a valid CSG object. The rotation of the rectangle around its normal is defined by `rotationvec`. `rotationvec×surfacenormal` is taken as the vector along the u axis.

**Can be used as a detector in [`AbstractOpticalSystem`](@ref)s.**

```julia
Rectangle(halfsizeu::T, halfsizev::T, [surfacenormal::SVector{3,T}, centrepoint::SVector{3,T}]; rotationvec::SVector{3,T} = [0.0, 1.0, 0.0], interface::NullOrFresnel{T} = nullinterface(T))
```

The minimal case returns a rectangle centered at the origin with `surfacenormal = [0, 0, 1]`.
