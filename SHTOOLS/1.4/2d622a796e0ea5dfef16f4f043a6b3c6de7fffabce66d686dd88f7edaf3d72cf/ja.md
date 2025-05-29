```
latglq, longlq, nlat, nlong =
    GLQGridCoord(lmax::Integer;
                 extend::Integer=0,
                 exitstatus::Union{Nothing,Ref{<:Integer}}=nothing)
latglq::Vector{Cdouble},
longlq::Vector{Cdouble},
nlat::Int
nlong::Int
```

ガウス・レジェンドル数値積分グリッドで使用される緯度と経度の座標を計算します。

参照: [`GLQGridCoord!`](@ref), [`SHExpandGLQ`](@ref), [`MakeGridGLQ`](@ref)
