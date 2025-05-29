```julia
function membership(stat::OneSampStatistic, ns::Int)
```

`OneSampStatistic` [グループ](@ref "Statistic groups") に属する検定統計量の置換スキームを使用して、[独自のテストを作成する](@ref "Create your own test") ときに、関数 [`_permTest!`](@ref) および [`_permMcTest!`](@ref) で使用される適切な引数 `x` を作成します。

`stat` が `OneSampStatistic` であり、`ns` は整数として与えられる観察数（例：*被験者*）です。詳細は [ns](@ref) を参照してください。

`ones(Int, ns)` を返します。

*例*

```julia
using PermutationsTests
membership(Sum(), 5)
# return the vector [1, 1, 1, 1, 1]
```
