```julia
function statistic(x::IntVec, y::UniData, stat::SumGroupTotalsSq_IS; 
                k::Into=nothing, 
                kwargs...)
```

平方和のグループ合計の合計。

バランスの取れたデザインにおける独立サンプルの1-way ANOVA *F* テスト統計量に相当します。詳細は[Statistic](@ref)を参照してください。

オプションのキーワード引数 `k` については、上記の`AnovaF_IS`の[`statistic`](@ref)メソッドを参照してください。
