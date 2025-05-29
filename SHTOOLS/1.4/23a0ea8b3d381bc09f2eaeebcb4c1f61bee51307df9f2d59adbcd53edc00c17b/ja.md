```
grid, nlat, nlong =
    MakeGrid2d(cilm::AbstractArray{Cdouble,3},
               lmax::Integer,
               interval::Union{AbstractFloat,Integer};
               norm::Integer=1,
               csphase::Integer=1,
               f::Optional{Union{AbstractFloat,Integer}}=nothing,
               a::Optional{Union{AbstractFloat,Integer}}=nothing,
               north::Union{AbstractFloat,Integer}=90.0,
               south::Union{AbstractFloat,Integer}=-90.0,
               east::Union{AbstractFloat,Integer}=360.0,
               west::Union{AbstractFloat,Integer}=0.0,
               dealloc::Bool=false,
               exitstatus::Optional{Ref{<:Integer}}=nothing)
grid::Array{Cdouble,2}
nlat::Int
nlong::Int
```

球面調和係数のセットから任意のグリッド間隔を持つ2D円筒マップを作成します。

参照: [`MakeGrid2d!`](@ref), [`MakeGridPoint`](@ref)
