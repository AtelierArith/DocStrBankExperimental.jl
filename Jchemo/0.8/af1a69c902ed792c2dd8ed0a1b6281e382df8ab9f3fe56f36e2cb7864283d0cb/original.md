```
calpds(; npoint = 5, algo = plskern, kwargs...)
calpds(X1, X2; npoint = 5, algo = plskern, kwargs...)
```

Piecewise direct standardization (PDS) for calibration transfer of spectral data.

  * `X1` : Spectra (n, p) to transfer to the target.
  * `X2` : Target spectra (n, p).

Keyword arguments:

  * `npoint` : Half-window size (nb. points left or right    to the given wavelength).
  * `algo` : Function used as transfer model.
  * `kwargs` : Optional arguments for `algo`.

`X1` and `X2` must represent the same n standard samples.

The objective is to transform spectra `X1` to new spectra as close  as possible as the target `X2`. Method PDS fits models  (defined in `algo`) that predict `X2` from `X1`.

The window used in `X1` to predict wavelength "i" in `X2` is:

  * i - `npoint`, i - `npoint` + 1, ..., i, ..., i + `npoint` - 1, i + `npoint`

## References

Bouveresse, E., Massart, D.L., 1996. Improvement of the piecewise direct targetisation procedure  for the transfer of NIR spectra for multivariate calibration. Chemometrics and Intelligent Laboratory  Systems 32, 201–213. https://doi.org/10.1016/0169-7439(95)00074-7

Y. Wang, D. J. Veltkamp, and B. R. Kowalski, “Multivariate Instrument Standardization,”  Anal. Chem., vol. 63, no. 23, pp. 2750–2756, 1991, doi: 10.1021/ac00023a016.

Wülfert, F., Kok, W.Th., Noord, O.E. de, Smilde, A.K., 2000. Correction of Temperature-Induced  Spectral Variation by Continuous Piecewise Direct Standardization. Anal. Chem. 72, 1639–1644. https://doi.org/10.1021/ac9906835

## Examples

```julia
using Jchemo, JchemoData, JLD2, CairoMakie
path_jdat = dirname(dirname(pathof(JchemoData)))
db = joinpath(path_jdat, "data/caltransfer.jld2")
@load db dat
@names dat
## Objects X1 and X2 are spectra collected 
## on the same samples. 
## X2 represents the target space. 
## We want to transfer X1 in the same space
## as X2.
## Data to transfer
X1cal = dat.X1cal
X1val = dat.X1val
n = nro(X1cal)
m = nro(X1val)
## Target space
X2cal = dat.X2cal
X2val = dat.X2val

## Fitting the model
fitm = calpds(X1cal, X2cal; npoint = 2, algo = plskern, nlv = 2) 

## Transfer of new spectra X1val 
## expected to be close to X2val
pred = predict(fitm, X1val).pred

i = 1
f = Figure(size = (500, 300))
ax = Axis(f[1, 1])
lines!(X2val[i, :]; label = "x2")
lines!(ax, X1val[i, :]; label = "x1")
lines!(pred[i, :]; linestyle = :dash, label = "x1_corrected")
axislegend(position = :rb, framevisible = false)
f
```
