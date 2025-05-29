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

スカラー関数の勾配を計算し、DriscollとHealy（1994）のサンプリング定理に準拠した2つの水平成分のグリッドを返します。

関連情報: [`MakeGradientDH!`](@ref), [`SHExpandDH`](@ref), [`MakeGridDH`](@ref)
