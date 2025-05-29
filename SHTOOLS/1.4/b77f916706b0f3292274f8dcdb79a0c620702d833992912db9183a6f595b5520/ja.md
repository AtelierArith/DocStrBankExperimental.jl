```
cilmout = SHMultiply(cilm1::AbstractArray{Cdouble,3},
                     lmax1::Integer,
                     cilm2::AbstractArray{Cdouble,3},
                     lmax2::Integer;
                     precomp::Bool=false,
                     norm::Integer=1,
                     csphase::Integer=1,
                     exitstatus::Optional{Ref{<:Integer}}=nothing)
cilmout::Array{Cdouble,3}
```

2つの関数を掛け合わせ、結果の関数の球面調和係数を決定します。

参照: [`SHMultiply!`](@ref), [`SHExpandDH`](@ref), [`SHExpandGLQ`](@ref), [`SHExpandLSQ`](@ref)
