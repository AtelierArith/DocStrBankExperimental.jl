```julia
function statistic(x::UniData, y::UniData, stat::CrossProd; 
                kwargs...)
```

Cross-product (inner product) of data input vectors x and y.

Equivalent to the Pearson correlation *r* test statistic for directional correlation tests and always  if the data is standardized, see [Statistic](@ref).

*Examples*

```julia
using PermutationTests
x, y = randn(10), randn(10)
c = statistic(x, y, CrossProd())
```
