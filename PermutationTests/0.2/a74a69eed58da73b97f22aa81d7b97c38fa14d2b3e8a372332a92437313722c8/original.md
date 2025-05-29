```julia
function statistic(x::UniData, y::UniData, stat::StudentT_1S; 
                ∑y²::Realo=nothing, 
                kwargs...)
```

Student's one-sample *t* statistic.

`y` is the input data.

`x` is the [`membership(::OneSampStatistic)`](@ref) vector.

`∑y²` can be optionally provided to speed up computations since this quantity is invariant by data permutations. The exported function `_∑y²` can be used for this purpose,  see the examples below. 

*Examples*

```julia
using PermutationsTest
y=randn(6);
x=membership(StudentT_1S(), length(y));
t=statistic(x, y, StudentT_1S()) 

pcd=_∑y²(y)
t2=statistic(x, y, StudentT_1S(); ∑y²=pcd) 
println(t≈t2 ? "OK" : "Error")
```
