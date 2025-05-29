```
cilm = SHExpandGLQ(lmax::Integer,
                   gridglq::AbstractArray{Cdouble,2},
                   w::AbstractVector{Cdouble},
                   plx::Union{Nothing,AbstractArray{Cdouble,2}},
                   zero::Union{Nothing,AbstractVector{Cdouble}};
                   norm::Integer=1,
                   csphase::Integer=1,
                   lmax_calc::Union{Nothing,Integer}=nothing,
                   exitstatus::Union{Nothing,Ref{<:Integer}}=nothing)
cilm::Array{Cdouble,3},

cilm = SHExpandGLQ(lmax::Integer,
                   gridglq::AbstractArray{Complex{Cdouble},2},
                   w::AbstractVector{Cdouble},
                   plx::Union{Nothing,AbstractArray{Cdouble,2}},
                   zero::Union{Nothing,AbstractVector{Cdouble}};
                   norm::Integer=1,
                   csphase::Integer=1,
                   lmax_calc::Union{Nothing,Integer}=nothing,
                   exitstatus::Union{Nothing,Ref{<:Integer}}=nothing)
cilm::Array{Complex{Cdouble},3},
```

2Dの実数または複素数のマップをガウス・ルジャンドルの数値積分ノードでサンプリングし、実数または複素数の球面調和関数に展開します。

参照: [`SHExpandGLQ!`](@ref), [`SHGLQ`](@ref), [`MakeGridGLQ`](@ref), [`GLQGridCoord`](@ref)
