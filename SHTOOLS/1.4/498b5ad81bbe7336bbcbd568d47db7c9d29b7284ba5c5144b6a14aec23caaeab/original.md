```
MakeGridDH!(griddh::AbstractArray{Cdouble,2},
            cilm::AbstractArray{Cdouble,3},
            lmax::Integer;
            norm::Integer=1,
            sampling::Integer=1,
            csphase::Integer=1,
            lmax_calc::Union{Nothing,Integer}=nothing,
            extend::Integer=0,
            exitstatus::Union{Nothing,Ref{<:Integer}}=nothing)
griddh::AbstractArray{Cdouble,2}
n::Int

MakeGridDH!(griddh::AbstractArray{Complex{Cdouble},2},
            cilm::AbstractArray{Complex{Cdouble},3},
            lmax::Integer;
            norm::Integer=1,
            sampling::Integer=1,
            csphase::Integer=1,
            lmax_calc::Union{Nothing,Integer}=nothing,
            extend::Integer=0,
            exitstatus::Union{Nothing,Ref{<:Integer}}=nothing)
griddh::AbstractArray{Complex{Cdouble},2}
n::Int
```

Create a real or complex 2D map from a set of real or complex spherical harmonic coefficients that conforms with Driscoll and Healy’s (1994) sampling theorem.

See also: [`SHExpandDH!`](@ref), [`MakeGridDH`](@ref), [`MakeGradientDH!`](@ref)
