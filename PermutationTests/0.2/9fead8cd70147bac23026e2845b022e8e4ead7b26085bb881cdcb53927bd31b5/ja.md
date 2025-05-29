```julia
function eqStat(stat, direction::TestDir, design::Assign) 
    where {TestDir<: TestDirection, Assign <: Assignment}
```

与えられた単一の `direction` の型 [TestDirection](@ref) と単一の `design` の型 [Assignment](@ref) に対して、`stat` に最も効率的な統計量を返します。

`stat` は、5つの典型的な検定統計量のいずれかの単一のものであり、すなわち `PearsonR()`, `AnovaF_IS()`, `StudentT_IS`, `AnovaF_RM()` または `StudentT_1S()` です。詳細は [Statistic](@ref) を参照してください。

エラーを避けるために、引数 `design` として [`assignment`](@ref) の結果を使用してください。

`stat` として `StudentT_RM()` を使用しないでください。*PermutationTests.jl* はこの検定統計量を使用しません。代わりに、繰り返し測定のt検定は、2つの測定の差に対する1標本t検定として実施されます。

*例*

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
