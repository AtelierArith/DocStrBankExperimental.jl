```
fdif(; kwargs...)
fdif(X; kwargs...)
```

Finite differences (discrete derivates) for each row of X-data. 

  * `X` : X-data (n, p).

Keyword arguments:

  * `npoint` : Nb. points involved in the window for the    finite differences. The range of the window    (= nb. intervals of two successive colums) is npoint - 1.

The method reduces the column-dimension: 

  * (n, p) –> (n, p - npoint + 1).

## Examples

```julia
using Jchemo, JchemoData, JLD2, CairoMakie
path_jdat = dirname(dirname(pathof(JchemoData)))
db = joinpath(path_jdat, "data/cassav.jld2") 
@load db dat
@names dat
X = dat.X
year = dat.Y.year
s = year .<= 2012
Xtrain = X[s, :]
Xtest = rmrow(X, s)
wlst = names(dat.X)
wl = parse.(Float64, wlst)
plotsp(X, wl; nsamp = 20).f

model = fdif(npoint = 2) 
fit!(model, Xtrain)
Xptrain = transf(model, Xtrain)
Xptest = transf(model, Xtest)
plotsp(Xptrain).f
plotsp(Xptest).f
```
