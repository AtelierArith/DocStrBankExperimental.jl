```
cindex = SHCilmToCindex!(cindex::AbstractArray{Cdouble,2},
                         cilm::AbstractArray{Cdouble,3};
                         degmax::Optional{Cint}=nothing,
                         exitstatus::Optional{Ref{<:Integer}}=nothing)
cindex::AbstractArray{Cdouble,2}
```

三次元の球面調和係数の配列を二次元のインデックス配列に変換します。

参照: [`SHCilmToCindex`](@ref), [`SHCindexToCilm!`](@ref), [`SHCilmToVector!`](@ref)
