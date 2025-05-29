```
LensTrace{T<:Real,N}
```

Contains an intersection point and the ray segment leading to it from within an optical trace. The ray carries the path length, power, wavelength, number of intersections and source number, all of which are accessible directly on this class too.

Has the following accessor methods:

```julia
ray(a::LensTrace{T,N}) -> OpticalRay{T,N}
intersection(a::LensTrace{T,N}) -> Intersection{T,N}
power(a::LensTrace{T,N}) -> T
wavelength(a::LensTrace{T,N}) -> T
pathlength(a::LensTrace{T,N}) -> T
point(a::LensTrace{T,N}) -> SVector{N,T}
uv(a::LensTrace{T,N}) -> SVector{2,T}
sourcenum(a::LensTrace{T,N}) -> Int
nhits(a::LensTrace{T,N}) -> Int
```
