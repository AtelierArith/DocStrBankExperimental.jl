```julia
function statistic(x::UniData, y::UniData, stat::PearsonR; 
                standardized::Bool=false, 
                centered::Bool=false, 
                means::Tuple=(), 
                sds::Tuple=(), kwargs...)
```

Pearson product-moment correlation *r* statistic of input data vector `x` and `y`. 

If the means and/or standard deviations of `x` and `y` are passed as tuple `means` and `sds`, respectively, they are not computed.

If `centered` is true, the two vectors are assumed to have zero mean.

If `standardized` is true both x and y are assumed standardized,  thus only the cross-product needs to be computed. This is by far the most efficient way  if this function is to be called repeatedly on the same data input vectors and for computing p-values by data permutations as the cross-product is en equivalent test statistic for the Pearson correlation  if the data is standardized.

*Examples*

```julia
using PermutationTests
x, y = randn(10), randn(10);
c1 = statistic(x, y, PearsonR())

zx=μ0σ1(x);
zy=μ0σ1(y);
c2 = statistic(zx, zy, PearsonR(); standardized=true)
```

see [`μ0σ1`](@ref)
