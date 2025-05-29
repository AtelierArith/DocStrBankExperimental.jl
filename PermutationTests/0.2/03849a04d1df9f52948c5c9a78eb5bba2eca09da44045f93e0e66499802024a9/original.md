```julia
function trendTest!(<same args and kwargs as `correlationTest!`>)
```

Actually aliases for [`correlationTest`](@ref) and [`correlationTest!`](@ref), respectively.

The two vectors `x` and `y` of $N$ elements each are provided as data input.  `x` is a specified trend and `y` holds the observed data. A Pearson product-moment correlation test between  `x` and `y` is then carried out. 

`x` can hold any trend, such as linear, polynomial, exponential, logarithmic, power, trigonometric...

*Directional tests, permutation scheme and number of permutations for exact tests:* as per [`correlationTest`](@ref)

Multiple comparisons versions: [`trendMcTest`](@ref) and [`trendMcTest!`](@ref)

Both methods return a [UniTest](@ref) structure.

*Examples*

```julia
using PermutationTests
# We are goint to test an upward linear trend
N=10
x=Float64.(collect(Base.OneTo(N))) # [1, 2, ..., N]
y=[1., 2., 4., 3., 5., 6., 7., 8., 10., 9.]
# Supposing we expect an upward linear trend, 
# hence the correlation is expected to be positive,
# we can use a right-directional test to increase the power of the test.
t = trendTest(x, y; direction=Right()) 
```
