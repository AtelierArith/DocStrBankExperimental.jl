```julia
function assignment(stat::Union{BivStatistic, OneSampStatistic}, ns::Int) 

function assignment(stat::IndSampStatistic, ns::Vector{Int}) 

function assignment(stat::RepMeasStatistic, ns::@NamedTuple{n::Int, k::Int})
```

テスト統計量として与えられた単一の `stat` に対する [ns](@ref) 引数を分析し、タイプ [Assignment](@ref) の単一の値を返します。デザインがバランスが取れている場合は `Balanced()` を、そうでない場合は `Unbalanced()` を返します。

`IndSampStatistic` のテスト統計量に対してのみ、結果は `Unbalanced()` になる可能性があります。他のすべての場合、結果は常に `Balanced()` です。

テスト統計量の完全なリストは [here](@ref "Statistics") にあります。

*例*

```julia
using PermutationTests
assignment(PearsonR(), 12) # -> Balanced()
assignment(AnovaF_IS(), [5, 5, 6]) # -> Unbalanced()
assignment(AnovaF_IS(), [6, 6, 6]) # -> Balanced()
assignment(StudentT_IS(), [5, 6]) # -> Unbalanced()
assignment(StudentT_IS(), [5, 5]) # -> Balanced()
assignment(AnovaF_RM(), (n=10, k=3)) # -> Balanced()
assignment(StudentT_1S(), 8) # -> Balanced()
```
