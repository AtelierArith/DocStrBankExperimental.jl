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

実数または複素数の球面調和係数のセットから、ガウス・レジェンドルの数値積分ノードでサンプリングされた2D実数または複素数マップを作成します。

参照: [`MakeGridGLQ!`](@ref), [`SHGLQ`](@ref), [`SHExpandGLQ`](@ref), [`GLQGridCoord`](@ref)
