```julia
function assignment(stat::Union{BivStatistic, OneSampStatistic}, ns::Int) 

function assignment(stat::IndSampStatistic, ns::Vector{Int}) 

function assignment(stat::RepMeasStatistic, ns::@NamedTuple{n::Int, k::Int})
```

Analyse the [ns](@ref) argument for test statistic given as singleton `stat` and return a  singleton of type [Assignment](@ref), `Balanced()` if the design is balanced  (equal subjects in all groups/measurements), `Unbalanced()` otherwise. 

Only for test-statistics of the `IndSampStatistic` [group](@ref "Statistic groups") the result may be `Unbalanced()`;  for all the others the result is always `Balanced()`. 

The complete list of test statistics is [here](@ref "Statistics").

*Examples*

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
