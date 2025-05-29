```
cilm, chi = SHExpandLSQ(d::AbstractVector{Cdouble},
                        lat::AbstractVector{Cdouble},
                        lon::AbstractVector{Cdouble},
                        nmax::Integer,
                        lmax::Integer;
                        norm::Integer=1,
                        csphase::Integer=1,
                        weights::Vector{Cdouble},
                        exitstatus::Optional{Ref{<:Integer}}=nothing)
cilm::Array{Cdouble,3},
chi::Cdouble
```

不規則にサンプリングされたデータポイントのセットを球面調和関数に展開します（加重最小二乗逆行列を使用）。

参照: [`SHExpandLSQ!`](@ref), [`MakeGridPoint`](@ref), [`SHExpandDH`](@ref), [`SHExpandGLQ`](@ref)
