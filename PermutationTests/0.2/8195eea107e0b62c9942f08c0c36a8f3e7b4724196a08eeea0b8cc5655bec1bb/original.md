```julia
function trendMcTest!(<same args and kwargs as correlationMcTest!>)
```

Actually aliases of [`correlationMcTest`](@ref) and [`correlationMcTest!`](@ref), respectively. 

`x` is any specified trend (linear, polynomial, exponential, logarithmic, trigonometric, ...) and `Y` holds the observed data. A multiple comparison Pearson product-moment correlation  test between `x` and all $M$ vectors in `Y` is then carried out. 

Directional tests, permutation scheme and number of permutations for exact tests: as per  *univariate versions* [`trendTest`](@ref) or [`trendTest!`](@ref)

Both methods return a [MultcompTest](@ref) structure.

*Examples*

```julia
using PermutationTests
# We are goint to test an upward linear trend
N=10
M=100
x=Float64.(collect(Base.OneTo(N))) # [1, 2,..., N]
# out of the M vectors created here below, only one has a significant correlation
Y=[[1., 2., 4., 3., 5., 6., 7., 8., 10., 9.], ([randn(N) for m=1:M-1]...)];
# Since we expect an upward linear trend, the correlation is expected to be positive,
# hence we use a right-directional test to increase the power of the test.
t = trendMcTest(x, Y; direction=Right()) 
```
