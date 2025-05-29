```julia
function statistic(x::UniData, y::UniData, stat::Covariance; 
                centered::Bool=false, 
                means::Tuple=(), 
                kwargs...)
```

Covariance of data input vectors x and y.

Equivalent to the Pearson correlation *r* test statistic for bi-directional correlation tests,  see [Statistic](@ref).

For the optional keyword arguments, see the method [`statistic(x, y, stat::PearsonR)`](@ref).

*Examples*

```julia
using PermutationTests
x, y = randn(10), randn(10)
c1 = statistic(x, y, Covariance())

c2 = statistic(μ0(x), μ0(y), Covariance(); centered=true)

μx=μ(x)
μy=μ(y)
c3 = statistic(x, y, Covariance(); means=(μx, μy))
```

see [`μ0`](@ref), [`μ`](@ref) 
