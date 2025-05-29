```
cglsr(; kwargs...)
cglsr(X, y; kwargs...)
cglsr!(X::Matrix, y::Matrix; kwargs...)
```

Conjugate gradient algorithm for the normal equations (CGLS; Björck 1996).

  * `X` : X-data  (n, p).
  * `y` : Univariate Y-data (n).

Keyword arguments:

  * `nlv` : Nb. CG iterations.
  * `gs` : Boolean. If `true` (default), a Gram-Schmidt    orthogonalization of the normal equation    residual vectors is done.
  * `filt` : Boolean. If `true`, CG filter factors    are computed (output `F`). Default = `false`.
  * `scal` : Boolean. If `true`, each column of `X`    is scaled by its uncorrected standard deviation.

CGLS algorithm "7.4.1" Bjorck 1996, p.289. In the present function, the  part of the code computing the re-orthogonalization (Hansen 1998) and  filter factors (Vogel 1987, Hansen 1998) is a transcription  (with few adaptations) of the Matlab function `cgls` (Saunders et al.  https://web.stanford.edu/group/SOL/software/cgls/; Hansen 2008).

## References

Björck, A., 1996. Numerical Methods for Least Squares Problems,  Other Titles in Applied Mathematics. Society for Industrial and Applied  Mathematics. https://doi.org/10.1137/1.9781611971484

Hansen, P.C., 1998. Rank-Deficient and Discrete Ill-Posed Problems,  Mathematical Modeling and Computation. Society for Industrial and Applied  Mathematics. https://doi.org/10.1137/1.9780898719697

Hansen, P.C., 2008. Regularization Tools version 4.0 for Matlab 7.3.  Numer Algor 46, 189–194. https://doi.org/10.1007/s11075-007-9136-9

Manne R. Analysis of two partial-least-squares algorithms for  multivariate calibration. Chemometrics Intell. Lab. Syst. 1987, 2: 187–197.

Phatak A, De Hoog F. Exploiting the connection between PLS,  Lanczos methods and conjugate gradients: alternative proofs  of some properties of PLS. J. Chemometrics 2002; 16: 361–367.

Vogel, C. R.,  "Solving ill-conditioned linear systems using  the conjugate gradient method", Report, Dept. of Mathematical  Sciences, Montana State University, 1987.

## Examples

```julia
using Jchemo, JchemoData, JLD2, CairoMakie
mypath = dirname(dirname(pathof(JchemoData)))
db = joinpath(mypath, "data", "cassav.jld2") 
@load db dat
@names dat
X = dat.X 
y = dat.Y.tbc
year = dat.Y.year
tab(year)
s = year .<= 2012
Xtrain = X[s, :]
ytrain = y[s]
Xtest = rmrow(X, s)
ytest = rmrow(y, s)

nlv = 5 ; scal = true
model = cglsr(; nlv, scal)
fit!(model, Xtrain, ytrain)
@names model.fitm 
@head model.fitm.B
coef(model.fitm).B
coef(model.fitm).int

pred = predict(model, Xtest).pred
@show rmsep(pred, ytest)
plotxy(vec(pred), ytest; color = (:red, .5), bisect = true, xlabel = "Prediction", 
    ylabel = "Observed").f   
```
