```
latglq, longlq, nlat, nlong =
    GLQGridCoord!(latglq::AbstractVector{Cdouble},
                  longlq::AbstractVector{Cdouble},
                  lmax::Integer;
                  extend::Integer=0,
                  exitstatus::Union{Nothing,Ref{<:Integer}}=nothing)
latglq::AbstractVector{Cdouble},
longlq::AbstractVector{Cdouble},
nlat::Int
nlong::Int
```

ガウス・レジェンドル数値積分グリッドで使用される緯度と経度の座標を計算します。

参照: [`GLQGridCoord`](@ref), [`SHExpandGLQ!`](@ref), [`MakeGridGLQ!`](@ref)
