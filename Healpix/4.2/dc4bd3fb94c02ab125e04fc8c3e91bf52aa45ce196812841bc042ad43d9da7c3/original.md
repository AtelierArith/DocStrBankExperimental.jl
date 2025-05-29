```
AbstractHealpixMap{T} <: AbstractArray{T, 1}
```

An abstract type representing an Healpix map without a specified ordering. This can be used to implement multiple dispatch when you don't care about the ordering of a map.
