```
gridglq = MakeGridGLQ!(gridglq::AbstractArray{Cdouble,2},
                       cilm::AbstractArray{Cdouble,3},
                       lmax::Integer,
                       plx::Union{Nothing,AbstractArray{Cdouble,2}},
                       zero::Union{Nothing,AbstractVector{Cdouble}};
                       norm::Integer=1,
                       csphase::Integer=1,
                       lmax_calc::Union{Nothing,Integer}=nothing,
                       extend::Integer=0,
                       exitstatus::Union{Nothing,Ref{<:Integer}}=nothing)
gridqlq::AbstractArray{Cdouble,2}

gridglq = MakeGridGLQ!(gridglq::AbstractArray{Complex{Cdouble},2},
                       cilm::AbstractArray{Complex{Cdouble},3},
                       lmax::Integer,
                       plx::Union{Nothing,AbstractArray{Cdouble,2}},
                       zero::Union{Nothing,AbstractVector{Cdouble}};
                       norm::Integer=1,
                       csphase::Integer=1,
                       lmax_calc::Union{Nothing,Integer}=nothing,
                       extend::Integer=0,
                       exitstatus::Union{Nothing,Ref{<:Integer}}=nothing)
gridqlq::AbstractArray{Complex{Cdouble},2}
```

実数または複素数の球面調和係数のセットから、ガウス・レジェンドル数値積分ノード上でサンプリングされた2D実数または複素数マップを作成します。

参照: [`MakeGridGLQ`](@ref), [`SHGLQ!`](@ref), [`SHExpandGLQ!`](@ref), [`GLQGridCoord!`](@ref)
