```julia
function eqStat(stat, direction::TestDir, design::Assign) 
    where {TestDir<: TestDirection, Assign <: Assignment}
```

Return the most efficient statistic equivalent to `stat`, for the given  singleton `direction` of type [TestDirection](@ref) and singleton `design` of type [Assignment](@ref).

`stat` is a singleton of one of the five typical test statistics, that is, `PearsonR()`, `AnovaF_IS()`, `StudentT_IS`, `AnovaF_RM()` or  `StudentT_1S()`, see [Statistic](@ref).

To avoid errors, use the result of [`assignment`](@ref) as argument `design`. 

Do not use `StudentT_RM()` as `stat`; *PermutationTests.jl* never use this test statistic. instead, t-tests for repeated measures are carried out as one-sample t-tests on the difference of the two measurements. 

*Examples*

```julia
using PermutationTests
a=assignment
ns=12
eqStat(PearsonR(), Both(), a(PearsonR(), ns))       # -> Covariance()
eqStat(PearsonR(), Right(), a(PearsonR(), ns))      # -> CrossProd()
ns=[6, 6, 6]
eqStat(AnovaF_IS(), Both(), a(AnovaF_IS(), ns))     # -> SumGroupTotalsSq_IS()
ns=[6, 7, 6]
eqStat(AnovaF_IS(), Both(), a(AnovaF_IS(), ns))     # -> SumGroupTotalsSqN_IS()
ns=[6, 7]
eqStat(StudentT_IS(), Both(), a(StudentT_IS(), ns)) # -> SumGroupTotalsSqN_IS()
eqStat(StudentT_IS(), Left(), a(StudentT_IS(), ns)) # -> Group1Total_IS()
ns=(n=10, k=3)
eqStat(AnovaF_RM(), Both(), a(AnovaF_RM(), ns))     # -> SumTreatTotalsSq_RM()
eqStat(AnovaF_RM(), Right(), a(AnovaF_RM(), ns))    # -> SumTreatTotalsSq_RM()
ns=7
eqStat(StudentT_1S(), Both(), a(StudentT_1S(), ns)) # -> Sum()
eqStat(StudentT_1S(), Left(), a(StudentT_1S(), ns)) # -> Sum()
```
