```julia

# METHOD 1
function testStatistic(x, y, stat::mystat, fstat::Function; 
                        cpcd=nothing, kwargs...)

# METHOD 2
function testStatistic(x, Y, i::Int, stat::mystat, fstat::Function; 
                        cpcd=nothing, kwargs...)
                        
        where mystat<:Statistic 
```

Compute the observed and permuted test statistic for univariate tests (Method 1) or the $i^{th}$  observed and permuted test statistic for the $i^{th}$ hypothesis, with $i=1...M$,  for multiple comparisons permutation tests (Method 2).

If you [create your own test](@ref "Create your own test") you will write new methods for these functions taking as `stat` a test statistic of type [Statistic](@ref) you have declared.

If not, you never need these functions.

`Y` is a vector of elements (typically, vectors themelves) and the test-statistic is to be computed on `Y[i]`, using the permutation vector `x`.

For the `fstat` and `cpcd` argument, see how to [create your own test](@ref "Create your own test").
