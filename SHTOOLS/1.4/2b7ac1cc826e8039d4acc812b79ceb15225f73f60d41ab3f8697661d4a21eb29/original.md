```
value = MakeGridPoint(cilm::AbstractArray{Cdouble,3},
                      lmax::Integer,
                      lat::Union{AbstractFloat,Integer},
                      long::Union{AbstractFloat,Integer};
                      norm::Integer=1,
                      csphase::Integer=1,
                      dealloc::Bool=false)
value::Float64

value = MakeGridPoint(cilm::AbstractArray{Complex{Cdouble},3},
                      lmax::Integer,
                      lat::Union{AbstractFloat,Integer},
                      long::Union{AbstractFloat,Integer};
                      norm::Integer=1,
                      csphase::Integer=1,
                      dealloc::Bool=false)
value::Complex{Float64}
```

Evaluate a real or complex function expressed in real or complex spherical harmonics at a single point.

See also: [`SHExpandLSQ!`](@ref), [`SHExpandLSQ`](@ref), [`MakeGrid2d!`](@ref), [`MakeGrid2d`](@ref)
