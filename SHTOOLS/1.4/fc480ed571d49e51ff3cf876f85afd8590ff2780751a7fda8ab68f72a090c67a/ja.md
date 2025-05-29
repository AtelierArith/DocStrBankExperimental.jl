```
cilm, chi = SHExpandLSQ!(cilm::AbstractArray{Cdouble,3},
                         d::AbstractVector{Cdouble},
                         lat::AbstractVector{Cdouble},
                         lon::AbstractVector{Cdouble},
                         nmax::Integer,
                         lmax::Integer;
                         norm::Integer=1,
                         csphase::Integer=1,
                         weights::Vector{Cdouble},
                         exitstatus::Optional{Ref{<:Integer}}=nothing)
cilm::AbstractArray{Cdouble,3},
chi::Float64
```

不規則にサンプリングされたデータポイントのセットを球面調和関数に展開します（加重最小二乗逆行列を使用）。

参照: [`SHExpandLSQ`](@ref), [`MakeGridPoint`](@ref), [`SHExpandDH!`](@ref), [`SHExpandGLQ!`](@ref)
