```
zero, w = SHGLQ!(zero::AbstractVector{Cdouble},
                 w::AbstractVector{Cdouble},
                 plx::Union{Nothing,AbstractArray{Cdouble,2}},
                 lmax::Integer;
                 norm::Integer=1,
                 csphase::Integer=1,
                 cnorm::Integer=0,
                 exitstatus::Union{Nothing,Ref{<:Integer}}=nothing)
zero::AbstractVector{Cdouble}
w::AbstractVector{Cdouble}
```

GLQベースの球面調和関数ルーチンで使用される重み、ノード、および関連するレジェンドル関数を事前計算します。

参照: [`SHGLQ`](@ref), [`SHExpandGLQ!`](@ref), [`MakeGridGLQ!`](@ref), [`GLQGridCoord!`](@ref)
