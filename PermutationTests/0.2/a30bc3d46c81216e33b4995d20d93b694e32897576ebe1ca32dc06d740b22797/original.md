```julia
function membership(stat::OneSampStatistic, ns::Int)
```

Create the appropriate argument `x` to be used by functions [`_permTest!`](@ref) and [`_permMcTest!`](@ref) when you  [create your own test](@ref "Create your own test") using the permutation scheme of test statistics belonging  to the `OneSampStatistic` [group](@ref "Statistic groups").

For `stat` a `OneSampStatistic`, `ns` is the number of observations (e.,g., *subjects*) given as an integer, see [ns](@ref).

Return `ones(Int, ns)`.

*Examples*

```julia
using PermutationsTests
membership(Sum(), 5)
# return the vector [1, 1, 1, 1, 1]
```
