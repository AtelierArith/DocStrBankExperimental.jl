```
Hexagon{T} <: Surface{T}
```

Hexagonal surface, not a valid CSG object. The rotation of the hexagon around its normal is defined by `rotationvec`. `rotationvec×surfacenormal` is taken as the vector along the u axis.

```julia
Hexagon(side_length::T, [surfacenormal::SVector{3,T}, centrepoint::SVector{3,T}]; rotationvec::SVector{3,T} = [0.0, 1.0, 0.0], interface::NullOrFresnel{T} = nullinterface(T))
```

The minimal case returns a rectangle centered at the origin with `surfacenormal = [0, 0, 1]`.
