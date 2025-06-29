```
viperm(model, X, Y; rep = 50, psamp = .3, score = rmsep)
```

Variable importance by direct permutations.

  * `model` : Model to evaluate.
  * `X` : X-data (n, p).
  * `Y` : Y-data (n, q).

Keyword arguments:

  * `rep` : Number of replications of the splitting   training/test.
  * `psamp` : Proportion of data used as test set    to compute the `score`.
  * `score` : Function computing the prediction score.

The principle is as follows:

  * Data (X, Y) are splitted randomly to a training and a test set.
  * The model is fitted on Xtrain, and the score (error rate)    is computed on Xtest. This gives the reference error rate.
  * Rows of a given variable (feature) j in Xtest are randomly    permutated (the rest of Xtest is unchanged). The score is computed    on the Xtest*perm*j (i.e. Xtest after thta the rows of variable j    were permuted). The importance of variable j is computed by the    difference between this score and the reference score.
  * This process is run for each variable j separately and replicated    `rep` times. Average results are provided in the outputs, as well    as the results per replication.

In general, this method returns similar results as the out-of-bag permutation  method used in random forests (Breiman, 2001).

## References

  * Nørgaard, L., Saudland, A., Wagner, J., Nielsen, J.V., Munck, L.,

Engelsen, S.B., 2000. Interval Partial Least-Squares Regression (iPLS):  A Comparative Chemometric Study with an Example from Near-Infrared  Spectroscopy. Appl Spectrosc 54, 413–419.  https://doi.org/10.1366/0003702001949500

## Examples

```julia
using Jchemo, JchemoData, JLD2, CairoMakie
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

model = plskern(nlv = 9)
res = viperm(model, Xtrain, ytrain; rep = 50, score = rmsep) ;
z = vec(res.imp)
f = Figure(size = (500, 400))
ax = Axis(f[1, 1]; xlabel = "Wavelength (nm)", ylabel = "Importance")
scatter!(ax, wl, vec(z); color = (:red, .5))
u = [910; 950]
vlines!(ax, u; color = :grey, linewidth = 1)
f

model = rfr(n_trees = 10, max_depth = 2000, min_samples_leaf = 5)
res = viperm(model, Xtrain, ytrain; rep = 50)
z = vec(res.imp)
f = Figure(size = (500, 400))
ax = Axis(f[1, 1];
    xlabel = "Wavelength (nm)", 
    ylabel = "Importance")
scatter!(ax, wl, vec(z); color = (:red, .5))
u = [910; 950]
vlines!(ax, u; color = :grey, linewidth = 1)
f
```
