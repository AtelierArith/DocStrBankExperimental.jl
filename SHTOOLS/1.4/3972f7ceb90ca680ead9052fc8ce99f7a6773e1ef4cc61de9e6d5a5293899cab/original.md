```
theta, phi, n = MakeGradientDH(cilm::AbstractArray{Cdouble,3},
                               lmax::Integer;
                               norm::Integer=1,
                               sampling::Integer=1,
                               csphase::Integer=1,
                               lmax_calc::Union{Nothing,Integer}=nothing,
                               extend::Integer=0,
                               exitstatus::Union{Nothing,Ref{<:Integer}}=nothing)
theta::Array{Cdouble,2}
phi::Array{Cdouble,2}
n::Int
```

Compute the gradient of a scalar function and return grids of the two horizontal components that conform with Driscoll and Healy’s (1994) sampling theorem.

See also: [`MakeGradientDH!`](@ref), [`SHExpandDH`](@ref), [`MakeGridDH`](@ref)
