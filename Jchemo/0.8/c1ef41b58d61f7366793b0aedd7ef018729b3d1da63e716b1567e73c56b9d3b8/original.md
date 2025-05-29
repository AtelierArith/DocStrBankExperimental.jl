```
aov1(x, Y)
One-factor ANOVA test.
```

  * `x` : Univariate categorical (factor) data (n).
  * `Y` : Y-data (n, q).

## Examples

```julia
using Jchemo, JchemoData, JLD2
path_jdat = dirname(dirname(pathof(JchemoData)))
db = joinpath(path_jdat, "data/iris.jld2") 
@load db dat
@names dat
@head dat.X
x = dat.X[:, 5]
Y = dat.X[:, 1:4]
tab(x) 

res = aov1(x, Y) ;
@names res
res.SSF
res.SSR 
res.F 
res.pval
```
