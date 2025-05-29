```julia
function statistic(x::Tuple, y::UniData, stat::StudentT_1S; 
                ∑y²::Realo=nothing, 
                kwargs...) 
```

Student's one-sample *t* statistic.

`y` is the input data.

`x` is a tuple holding as many 1.0 as elements in `y`.

`∑y²` can be optionally provided to speed up computations, since this quantity is invariant by data permutations. The exported function `_∑y²` can be used for this purpose,  see the examples below. 

*Examples*

```julia
using PermutationsTest
y=randn(6);
x=(1., 1., 1., 1., 1., 1.);
t=statistic(x, y, StudentT_1S()) 

pcd=_∑y²(y)
t2=statistic(x, y, StudentT_1S(); ∑y²=pcd) 
println(t≈t2 ? "OK" : "Error")
```
