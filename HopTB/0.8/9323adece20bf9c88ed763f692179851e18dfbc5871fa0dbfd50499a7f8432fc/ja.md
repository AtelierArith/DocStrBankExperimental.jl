```julia
getdEs(
    tm::AbstractTBModel,
    α::Integer,
    β::Integer,
    k::AbstractVector{<:Real}
) => dEs::Vector{Float64}
```

`tm`における`k`でのd^2 E / dkα dkβを計算します。`α`と`β`は直交方向です。

dEs[n]は、nが非縮退または完全に縮退している場合にのみ正しいです。

この関数はメモ化されており、関数の引数と結果は決して変更されるべきではありません。
