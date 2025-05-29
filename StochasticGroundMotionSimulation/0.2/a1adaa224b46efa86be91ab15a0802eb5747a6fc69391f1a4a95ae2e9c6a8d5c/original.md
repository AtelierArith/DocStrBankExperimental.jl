```
FourierParameters
```

Custom type for the parameters the Fourier amplitude spectrum. This type is comprised of source, path and site types, and so has a base constructor of: `FourierParameters(src::S, path::T, site::U) where {S<:SourceParameters, T<:PathParameters, U<:SiteParameters}`

See also: [`SourceParameters`](@ref), [`PathParameters`](@ref), [`SiteParameters`](@ref)
