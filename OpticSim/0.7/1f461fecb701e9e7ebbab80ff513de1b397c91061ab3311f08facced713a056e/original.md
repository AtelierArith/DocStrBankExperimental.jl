```
OpticalRay{T,N} <: AbstractRay{T,N}
```

Ray with power, wavelength and optical path length.

**NOTE**: we use monte carlo integration to get accurate results on the detector, this means that all rays essentially hit the detector with power = 1 and some rays are thrown away at any interface to correctly match the reflection/transmission at that interface. For inspection purposes we also track the 'instantaneous' power of the ray in the `power` field of the `OpticalRay`.

```julia
OpticalRay(ray::Ray{T,N}, power::T, wavelength::T, opl=zero(T))
OpticalRay(origin::SVector{N,T}, direction::SVector{N,T}, power::T, wavelength::T, opl=zero(T))
```

Has the following accessor methods:

```julia
ray(r::OpticalRay{T,N}) -> Ray{T,N}
direction(r::OpticalRay{T,N}) -> SVector{N,T}
origin(r::OpticalRay{T,N}) -> SVector{N,T}
power(r::OpticalRay{T,N}) -> T
wavelength(r::OpticalRay{T,N}) -> T
pathlength(r::OpticalRay{T,N}) -> T
sourcepower(r::OpticalRay{T,N}) -> T
nhits(r::OpticalRay{T,N}) -> Int
sourcenum(r::OpticalRay{T,N}) -> Int
```
