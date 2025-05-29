```
cilm = SHVectorToCilm(cilm::AbstractArray{Cdouble,3},
                      vector::AbstractVector{Cdouble},
                      lmax::Integer;
                      exitstatus::Union{Nothing,Ref{<:Integer}}=nothing)
cilm::Array{Cdouble,3}
```

1次元インデックス付きベクトルの実球面調和係数を3次元配列に変換します。

参照: [`SHVectorToCilm!`](@ref)
