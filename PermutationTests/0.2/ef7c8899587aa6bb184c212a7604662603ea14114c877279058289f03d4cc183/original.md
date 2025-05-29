```julia
function membership(stat::RepMeasStatistic, ns::@NamedTuple{n::Int, k::Int})
```

Create the appropriate argument `x` to be used by functions [`_permTest!`](@ref) and [`_permMcTest!`](@ref) when you  [create your own test](@ref "Create your own test") using the permutation scheme of test statistics belonging  to the `RepMeasStatistic` [group](@ref "Statistic groups").

For `stat` a `RepMeasStatistic`, `ns` is a named tuple, such as `(n=N, k=K)`, where $N$ is the number of observations (e.g., *subjects*) and $K$ the number of measurements (or *treatments*, *times*, ect.), see [ns](@ref).

Return `collect(1:N*K)`.

*Examples*

```julia
using PermutationsTests
membership(AnovaF_RM(), (n=2, k=4))
# return the vector [1, 2, 3, 4, 5, 6, 7, 8]
```
