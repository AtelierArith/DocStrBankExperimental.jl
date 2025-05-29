```
Ellipse{T} <: Surface{T}
```

Elliptical surface, not a valid CSG object. The rotation of the rectangle around its normal is defined by `rotationvec`. `rotationvec×surfacenormal` is taken as the vector along the u axis.

**Can be used as a detector in [`AbstractOpticalSystem`](@ref)s.**

```julia
Ellipse(halfsizeu::T, halfsizev::T, [surfacenormal::SVector{3,T}, centrepoint::SVector{3,T}]; interface::NullOrFresnel{T} = nullinterface(T))
```

The minimal case returns an ellipse centered at the origin with `surfacenormal = [0, 0, 1]`.
