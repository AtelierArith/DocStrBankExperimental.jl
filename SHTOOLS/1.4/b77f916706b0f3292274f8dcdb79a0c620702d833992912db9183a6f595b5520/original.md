```
cilmout = SHMultiply(cilm1::AbstractArray{Cdouble,3},
                     lmax1::Integer,
                     cilm2::AbstractArray{Cdouble,3},
                     lmax2::Integer;
                     precomp::Bool=false,
                     norm::Integer=1,
                     csphase::Integer=1,
                     exitstatus::Optional{Ref{<:Integer}}=nothing)
cilmout::Array{Cdouble,3}
```

Multiply two functions and determine the spherical harmonic coefficients of the resulting function.

See also: [`SHMultiply!`](@ref), [`SHExpandDH`](@ref), [`SHExpandGLQ`](@ref), [`SHExpandLSQ`](@ref)
