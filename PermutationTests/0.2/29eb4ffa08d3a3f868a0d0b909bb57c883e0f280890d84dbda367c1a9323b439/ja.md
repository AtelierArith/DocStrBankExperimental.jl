```julia
function statistic(x::IntVec, y::UniData, stat::SumTreatTotalsSq_RM; 
                ns::@NamedTuple{n::Int, k::Int}, 
                kwargs...)
```

平方和の治療合計の合計。

一般的に、繰り返し測定の1-way ANOVA *F* テスト統計量に相当します。詳細は[Statistic](@ref)を参照してください。

オプションのキーワード引数`ns`については、上記の`AnovaF_RM`の[`statistic`](@ref)メソッドを参照してください。
