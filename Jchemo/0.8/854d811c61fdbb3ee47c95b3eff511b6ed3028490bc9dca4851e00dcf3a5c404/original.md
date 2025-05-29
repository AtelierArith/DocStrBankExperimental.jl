```
isel!(model, X, Y, wl = 1:nco(X); rep = 1, nint = 5, psamp = .3, score = rmsep)
```

Interval variable selection.

  * `model` : Model to evaluate.
  * `X` : X-data (n, p).
  * `Y` : Y-data (n, q).
  * `wl` : Optional numeric labels (p, 1) of the X-columns.

Keyword arguments:  

  * `rep` : Number of replications of the splitting   training/test.
  * `nint` : Nb. intervals.
  * `psamp` : Proportion of data used as test set    to compute the `score`.
  * `score` : Function computing the prediction score.

The principle is as follows:

  * Data (X, Y) are splitted randomly to a training and a test set.
  * Range 1:p in `X` is segmented to `nint` intervals, when possible    of equal size.
  * The model is fitted on the training set and the score (error rate)    on the test set, firtsly accounting for all the p variables    (reference) and secondly for each of the `nint` intervals.
  * This process is replicated `rep` times. Average results are provided    in the outputs, as well the results per replication.

## References

  * Nørgaard, L., Saudland, A., Wagner, J., Nielsen, J.V., Munck, L.,

Engelsen, S.B., 2000. Interval Partial Least-Squares Regression (iPLS):  A Comparative Chemometric Study with an Example from Near-Infrared  Spectroscopy. Appl Spectrosc 54, 413–419.  https://doi.org/10.1366/0003702001949500

## Examples

```julia
using Jchemo, JchemoData, DataFrames, JLD2, CairoMakie
mypath = dirname(dirname(pathof(JchemoData)))
db = joinpath(mypath, "data", "tecator.jld2") 
@load db dat
@names dat
X = dat.X
Y = dat.Y 
wl_str = names(X)
wl = parse.(Float64, wl_str) 
ntot, p = size(X)
typ = Y.typ
namy = names(Y)[1:3]
plotsp(X, wl; xlabel = "Wavelength (nm)", ylabel = "Absorbance").f

s = typ .== "train"
Xtrain = X[s, :]
Ytrain = Y[s, namy]
Xtest = rmrow(X, s)
Ytest = rmrow(Y[:, namy], s)
ntrain = nro(Xtrain)
ntest = nro(Xtest)
ntot = ntrain + ntest
(ntot = ntot, ntrain, ntest)

## Work on the j-th y-variable 
j = 2
nam = namy[j]
ytrain = Ytrain[:, nam]
ytest = Ytest[:, nam]

model = plskern(nlv = 5)
nint = 10
res = isel!(model, Xtrain, ytrain, wl; rep = 30, nint) ;
res.res_rep
res.res0_rep
zres = res.res
zres0 = res.res0
f = Figure(size = (650, 300))
ax = Axis(f[1, 1], xlabel = "Wawelength (nm)", ylabel = "RMSEP_Val",
    xticks = zres.lo)
scatter!(ax, zres.mid, zres.y1; color = (:red, .5))
vlines!(ax, zres.lo; color = :grey, linestyle = :dash, linewidth = 1)
hlines!(ax, zres0.y1, linestyle = :dash)
f
```
