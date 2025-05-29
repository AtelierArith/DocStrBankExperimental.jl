```julia
function membership(stat::IndSampStatistic, ns::Vector{Int})
```

Create the appropriate argument `x` to be used by functions [`_permTest!`](@ref) and [`_permMcTest!`](@ref) when you  [create your own test](@ref "Create your own test") using the permutation scheme of test statistics belonging  to the `IndSampStatistic` [group](@ref "Statistic groups").

For `stat` a `IndSampStatistic`, `ns` is a group numerosity vector, *i.e.*, a vector of positive integers  `[N1,...,NK]`, where $K$ is the number of groups and $N_k$ is the number of observations for the $k^{th}$ group (see [ns](@ref)).  

Return the group membership vector `[repeat (1, N1);...; repeat(K, Nk)]`

If `rev=reverse` is passed as keyword argument, return instead group membership vector `[repeat (K, N1);...; repeat(1, Nk)]`. This is used to run t-tests for independent samples using the `PearsonR()` [Statistic](@ref), see for example [`studentTestIS`](@ref).

*Examples*

```julia
using PermutationsTests
membership(AnovaF_IS(), [3, 4])
# return the vector [1, 1, 1, 2, 2, 2, 2]
```
