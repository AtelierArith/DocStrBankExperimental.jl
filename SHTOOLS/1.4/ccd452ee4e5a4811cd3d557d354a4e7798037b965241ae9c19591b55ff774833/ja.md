```
SHCilmToVector!(vector::AbstractVector{Cdouble},
                cilm::AbstractArray{Cdouble,3},
                lmax::Integer;
                exitstatus::Union{Nothing,Ref{<:Integer}}=nothing)
```

実数球面調和係数の三次元配列を1次元インデックスベクトルに変換します。

参照: [`SHCilmToVector`](@ref)
