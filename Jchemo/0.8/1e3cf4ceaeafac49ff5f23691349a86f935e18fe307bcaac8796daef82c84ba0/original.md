```
detrend_asls(; kwargs...)
detrend_asls(X; kwargs...)
```

Baseline correction of each row of X-data by asymmetric      least squares algorithm (ASLS).

  * `X` : X-data (n, p).

Keyword arguments:

  * `lb` : Penalizing (smoothness) parameter "lambda".
  * `p` : Asymmetry parameter (0 < `p` << 1).
  * `tol` : Tolerance value for stopping the iterations.
  * `maxit` : Maximum number of iterations.
  * `verbose` : If `true`, nb. iterations are printed.

De-trend transformation: the function fits a baseline by ASLS (see Baek et al. 2015 section 2) for each observation and returns the residuals (= signals corrected from the baseline).

Generally `0.001 ≤ p ≤ 0.1` is a good choice (for a signal with positive peaks)  and `1e2 ≤ lb ≤ 1e9`, but exceptions may occur (Eilers & Boelens 2005).

## References

Baek, S.-J., Park, A., Ahn, Y.-J., Choo, J., 2015. Baseline correction using  asymmetrically reweighted penalized least squares smoothing. Analyst 140, 250–257.  https://doi.org/10.1039/C4AN01061B

Eilers, P. H., & Boelens, H. F. (2005). Baseline correction with asymmetric  least squares smoothing. Leiden University Medical Centre Report, 1(1).

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
lb = 1e5 ; p = .001
model = detrend_asls(; lb, p)
fit!(model, zX)
zXc = transf(model, zX)   # = corrected spectrum 
B = zX - zXc              # = estimated baseline
f, ax = plotsp(zX, wl)
lines!(wl, vec(B); color = :blue)
lines!(wl, vec(zXc); color = :black)
f
```
