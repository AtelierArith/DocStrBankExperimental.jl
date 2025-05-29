```
genBasisFuncText(bs::Union{AbstractVector{<:FloatingGTBasisFuncs{T, D}}, 
                           Tuple{Vararg{FloatingGTBasisFuncs{T, D}}}}; 
                 norm::Real=1.0, printCenter::Bool=true, 
                 groupCenters::Bool=true, roundDigits::Int=-1) where {T, D} -> 
Vector{String}
```

入力基底セット（`FloatingGTBasisFuncs`で構成される）のテキストを生成します。`norm`は追加の正規化係数です。`groupCenters`は、同じ中心を持つ基底関数をまとめるかどうかを決定します。
