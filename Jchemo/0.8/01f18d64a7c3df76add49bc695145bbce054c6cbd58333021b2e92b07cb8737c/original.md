```
detrend_pol(; kwargs...)
detrend_pol(X; kwargs...)
```

Baseline correction of each row of X-data by polynomial linear regression.

  * `X` : X-data (n, p).

Keyword arguments:

  * `degree` : Polynom degree.

De-trend transformation: the function fits a baseline by polynomial regression  for each observation and returns the residuals (= signals corrected from the baseline).

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

model = detrend_pol(degree = 2)
fit!(model, Xtrain)
Xptrain = transf(model, Xtrain)
Xptest = transf(model, Xtest)
plotsp(Xptrain, wl).f
plotsp(Xptest, wl).f

## Example on 1 spectrum
i = 2
zX = Matrix(X)[i:i, :]
model = detrend_pol(degree = 1)
fit!(model, zX)
zXc = transf(model, zX)   # = corrected spectrum 
B = zX - zXc            # = estimated baseline
f, ax = plotsp(zX, wl)
lines!(wl, vec(B); color = :blue)
lines!(wl, vec(zXc); color = :black)
f
```
