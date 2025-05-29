```julia
function statistic(x::IntVec, y::UniData, stat::SumGroupTotalsSqN_IS; 
                k::Into=nothing, 
                ns::Union{Vector{Int}, Nothing}=nothing, 
                kwargs...)
```

グループ合計の二乗の合計を各グループの数に割ったもの。

一般的に、独立したサンプルの1-way ANOVAの*F*検定統計量に相当します。詳細は[Statistic](@ref)を参照してください。

オプションのキーワード引数`k`と`ns`、および例については、上記の`AnovaF_IS`の[`statistic`](@ref)メソッドを参照してください。
