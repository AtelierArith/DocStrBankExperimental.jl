```
detrend_airpls(; kwargs...)
detrend_airpls(X; kwargs...)
```

Baseline correction of each row of X-data by adaptive iteratively      reweighted penalized least squares algorithm (AIRPLS).

  * `X` : X-data (n, p).

Keyword arguments:

  * `lb` : Penalizing (smoothing) parameter "lambda".
  * `maxit` : Maximum number of iterations.
  * `verbose` : If `true`, nb. iterations are printed.

De-trend transformation: the function fits a baseline by AIRPLS (see Zhang et al. 2010,  and Baek et al. 2015 section 2) for each observation and returns the residuals  (= signals corrected from the baseline).

## References

Baek, S.-J., Park, A., Ahn, Y.-J., Choo, J., 2015. Baseline correction using  asymmetrically reweighted penalized least squares smoothing. Analyst 140, 250–257.  https://doi.org/10.1039/C4AN01061B

Zhang, Z.-M., Chen, S., Liang, Y.-Z., 2010. Baseline correction using adaptive  iteratively reweighted penalized least squares. Analyst 135, 1138–1146.  https://doi.org/10.1039/B922045C

https://github.com/zmzhang/airPLS/tree/master 

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

## Example on 1 spectrum
i = 2
zX = Matrix(X)[i:i, :]
lb = 1e6
model = detrend_airpls(; lb)
fit!(model, zX)
zXc = transf(model, zX)   # = corrected spectrum 
B = zX - zXc              # = estimated baseline
f, ax = plotsp(zX, wl)
lines!(wl, vec(B); color = :blue)
lines!(wl, vec(zXc); color = :black)
f
```
