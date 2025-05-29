```
vector = SHCilmToVector(cilm::AbstractArray{Cdouble,3},
                        lmax::Integer;
                        exitstatus::Union{Nothing,Ref{<:Integer}}=nothing)
vector::Vector{Cdouble}
```

実数球面調和係数の三次元配列を1次元のインデックス付き配列に変換します。

関連情報: [`SHCilmToVector!`](@ref)
