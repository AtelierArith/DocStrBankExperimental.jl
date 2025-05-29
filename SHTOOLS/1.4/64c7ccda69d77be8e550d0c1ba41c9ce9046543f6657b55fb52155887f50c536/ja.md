```
cilm = SHCindexToCilm!(cilm::AbstractArray{Cdouble,3},
                       cindex::AbstractArray{Cdouble,2};
                       degmax::Optional{Cint}=nothing,
                       exitstatus::Optional{Ref{<:Integer}}=nothing)
cilm::AbstractArray{Cdouble,3},
```

二次元の球面調和係数のインデックス配列を三次元配列に変換します。

参照: [`SHCindexToCilm`](@ref), [`SHCilmToCindex!`](@ref), [`SHVectorToCilm!`](@ref)
