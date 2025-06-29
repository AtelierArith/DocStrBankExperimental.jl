```
eposvd(D; nlv = 1)
```

Compute an orthogonalization matrix for calibration transfer      of spectral data.

  * `D` : Data (m, p) containing the detrimental information    on which spectra (rows of a matrix X) have to be orthogonalized.

Keyword arguments:

  * `nlv` : Nb. of first loadings vectors of `D` considered for the    orthogonalization.

The objective is to remove some detrimental information  (e.g. humidity patterns in signals, multiple spectrometers, etc.)  from a X-dataset (n, p).  The detrimental information is defined  by the main row-directions computed from a matrix `D` (m, p). 

Function `eposvd` returns two objects:

  * `V` (p, `nlv`) : The matrix of the `nlv` first    loading vectors of the SVD decomposition (non centered PCA)    of `D`.
  * `M` (p, p) : The orthogonalization matrix, used    to orthogonolize a given matrix X to directions    contained in `V`.

Any matrix X can then be corrected from `D` by:

  * X_corrected = X * `M`.

Matrix `D` can be built from many methods. For instance,      two common methods are:

  * EPO (Roger et al. 2003, 2018): `D` is built from a set of    differences between spectra collected under different    conditions.
  * TOP (Andrew & Fearn 2004): Each row of `D` is the mean spectrum    computed for a given spectrometer instrument.

A particular situation is the following. Assume that `D` is  built from some differences between matrices X1 and X2, and that  a bilinear model (e.g. PLSR) is fitted on the data {X1*corrected, Y} where X1*corrected = X1 * `M`. To predict new data X2*new with  the fitted model, there is no need to correct X2*new.

# References

Andrew, A., Fearn, T., 2004. Transfer by orthogonal projection:  making near-infrared calibrations robust to between-instrument  variation. Chemometrics and Intelligent Laboratory Systems 72,  51–56. https://doi.org/10.1016/j.chemolab.2004.02.004

Roger, J.-M., Chauchard, F., Bellon-Maurel, V., 2003. EPO-PLS  external parameter orthogonalisation of PLS application to  temperature-independent measurement of sugar content of intact  fruits. Chemometrics and Intelligent Laboratory Systems 66,  191-204. https://doi.org/10.1016/S0169-7439(03)00051-0

Roger, J.-M., Boulet, J.-C., 2018. A review of orthogonal  projections for calibration. Journal of Chemometrics 32, e3045.  https://doi.org/10.1002/cem.3045

Zeaiter, M., Roger, J.M., Bellon-Maurel, V., 2006. Dynamic  orthogonal projection. A new method to maintain the on-line  robustness of multivariate calibrations. Application to NIR-based  monitoring of wine fermentations. Chemometrics and Intelligent  Laboratory Systems, 80, 227–235.  https://doi.org/10.1016/j.chemolab.2005.06.011

## Examples

```julia
using Jchemo, JchemoData, JLD2, CairoMakie
path_jdat = dirname(dirname(pathof(JchemoData)))
db = joinpath(path_jdat, "data/caltransfer.jld2")
@load db dat
@names dat
X1cal = dat.X1cal
X1val = dat.X1val
X2cal = dat.X2cal
X2val = dat.X2val

## The objective is to remove a detrimental 
## information (here, D) from spaces X1 and X2
D = X1cal - X2cal
nlv = 2
res = eposvd(D; nlv)
res.M # orthogonalization matrix
res.V # detrimental directions (columns of matrix V = loadings of D)

## Corrected Val matrices
X1val_c = X1val * res.M
X2val_c = X2val * res.M

i = 1
f = Figure(size = (800, 300))
ax1 = Axis(f[1, 1])
ax2 = Axis(f[1, 2])
lines!(ax1, X1val[i, :]; label = "x1")
lines!(ax1, X2val[i, :]; label = "x2")
axislegend(ax1, position = :cb, framevisible = false)
lines!(ax2, X1val_c[i, :]; label = "x1_correct")
lines!(ax2, X2val_c[i, :]; label = "x2_correct")
axislegend(ax2, position = :cb, framevisible = false)
f
```
