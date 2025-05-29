```
cilm, lmax = SHExpandDH!(cilm::AbstractArray{Cdouble,3},
                         griddh::AbstractArray{Cdouble,2},
                         n::Integer;
                         norm::Integer=1,
                         sampling::Integer=1,
                         csphase::Integer=1,
                         lmax_calc::Union{Nothing,Integer}=nothing,
                         exitstatus::Union{Nothing,Ref{<:Integer}}=nothing)
cilm::AbstractArray{Cdouble,3}
lmax:Int

cilm, lmax = SHExpandDH!(cilm::AbstractArray{Complex{Cdouble},3},
                         griddh::AbstractArray{Complex{Cdouble},2},
                         n::Integer;
                         norm::Integer=1,
                         sampling::Integer=1,
                         csphase::Integer=1,
                         lmax_calc::Union{Nothing,Integer}=nothing,
                         exitstatus::Union{Nothing,Ref{<:Integer}}=nothing)
cilm::AbstractArray{Complex{Cdouble},3}
lmax:Int
```

Expand an equally sampled or equally spaced real or complex map into real or complex spherical harmonics using Driscoll and Healy’s (1994) sampling theorem.

See also: [`SHExpandDH`](@ref), [`MakeGridDH!`](@ref), [`MakeGradientDH!`](@ref)
