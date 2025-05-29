```
cindex = SHCilmToCindex(cilm::AbstractArray{Cdouble,3};
                        degmax::Optional{Cint}=nothing,
                        exitstatus::Optional{Ref{<:Integer}}=nothing)
cindex::Array{Cdouble,2}
```

球面調和係数の三次元配列を二次元インデックス配列に変換します。

参照: [`SHCilmToCindex!`](@ref), [`SHCindexToCilm`](@ref), [`SHCilmToVector`](@ref)
