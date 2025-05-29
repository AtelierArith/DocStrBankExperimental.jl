```
interpl(; kwargs...)
interpl(X; kwargs...)
```

Sampling spectra by interpolation.

  * `X` : Matrix (n, p) of spectra (rows).

Keyword arguments:

  * `wl` : Values representing the column "names" of `X`.    Must be a numeric vector of length p, or an AbstractRange,   with growing values.
  * `wlfin` : Final values (within the range of `wl`) where to interpolate   each spectrum. Must be a numeric vector, or an AbstractRange,   with growing values.

The function implements a cubic spline interpolation using  package DataInterpolations.jl.

## References

Package DAtaInterpolations.jl https://github.com/PumasAI/DataInterpolations.jl https://htmlpreview.github.io/?https://github.com/PumasAI/DataInterpolations.jl/blob/v2.0.0/example/DataInterpolations.html

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

wlfin = range(500, 2400, length = 10)
#wlfin = collect(range(500, 2400, length = 10))
model = interpl(; wl, wlfin)
fit!(model, Xtrain)
Xptrain = transf(model, Xtrain)
Xptest = transf(model, Xtest)
plotsp(Xptrain).f
plotsp(Xptest).f
```
