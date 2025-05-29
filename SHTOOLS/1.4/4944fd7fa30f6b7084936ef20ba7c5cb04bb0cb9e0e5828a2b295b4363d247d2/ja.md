```
SHVectorToCilm!(cilm::AbstractArray{Cdouble,3},
                vector::AbstractVector{Cdouble},
                lmax::Integer;
                exitstatus::Union{Nothing,Ref{<:Integer}}=nothing)
```

1次元のインデックス付きベクトルの実球面調和係数を3次元配列に変換します。

関連情報: [`SHVectorToCilm`](@ref)
