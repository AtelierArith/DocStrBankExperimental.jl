```
gridglq = MakeGridGLQ(cilm::AbstractArray{Cdouble,3},
                      lmax::Integer,
                      plx::Union{Nothing,AbstractArray{Cdouble,2}},
                      zero::Union{Nothing,AbstractVector{Cdouble}};
                      norm::Integer=1,
                      csphase::Integer=1,
                      lmax_calc::Union{Nothing,Integer}=nothing,
                      extend::Integer=0,
                      exitstatus::Union{Nothing,Ref{<:Integer}}=nothing)
gridqlq::Array{Cdouble,2}

gridglq = MakeGridGLQ(cilm::AbstractArray{Complex{Cdouble},3},
                      lmax::Integer,
                      plx::Union{Nothing,AbstractArray{Cdouble,2}},
                      zero::Union{Nothing,AbstractVector{Cdouble}};
                      norm::Integer=1,
                      csphase::Integer=1,
                      lmax_calc::Union{Nothing,Integer}=nothing,
                      extend::Integer=0,
                      exitstatus::Union{Nothing,Ref{<:Integer}}=nothing)
gridqlq::Array{Complex{Cdouble},2}
```

Create a 2D real or complex map from a set of real or complex spherical harmonic coefficients sampled on a the Gauss-Legendre quadrature nodes.

See also: [`MakeGridGLQ!`](@ref), [`SHGLQ`](@ref), [`SHExpandGLQ`](@ref), [`GLQGridCoord`](@ref)
