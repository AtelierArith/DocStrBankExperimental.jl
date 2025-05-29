```julia
function dispersion(x::UniData; 
    centered::Bool=false, mean::Realo=nothing)
```

If `centered` is true, return the sum of the squares of the elements in `x`,

otherwise, 

if `mean` is provided return the sum of squared deviations of the elements in `x` from `mean`,

otherwise,

return the sum of squared deviations of the elements in `x` from their mean.

*Examples*

```julia
using PermutationTests
x=randn(10)
x0=μ0(x)
μx=μ(x)
m=μ(x)

# in decreasing order of efficiency
d1=dispersion(x0)
d2=dispersion(x, mean=μx)
d3=dispersion(x)
d1==d2==d3 # -> true
```
