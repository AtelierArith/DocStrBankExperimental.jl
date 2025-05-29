```
occstah(; kwargs...)
occstah(X; kwargs...)
```

One-class classification using the Stahel-Donoho outlierness.

  * `X` : Training X-data (n, p).

Keyword arguments:

  * `nlv` : Nb. random directions on which `X` is projected.
  * `cut` : Type of cutoff. Possible values are: `:mad`, `:q`.    See Thereafter.
  * `cri` : When `cut` = `:mad`, a constant. See thereafter.
  * `risk` : When `cut` = `:q`, a risk-I level. See thereafter.
  * `scal` : Boolean. If `true`, each column of `X`    is scaled such as in function `outstah`.

In this method, the outlierness `d` of a given observation is the Stahel-Donoho outlierness (see `?outstah`).

See function `occsd` for details on outputs.

## Examples

```julia
using Jchemo, JchemoData, JLD2, CairoMakie
path_jdat = dirname(dirname(pathof(JchemoData)))
db = joinpath(path_jdat, "data/challenge2018.jld2") 
@load db dat
@names dat
X = dat.X    
Y = dat.Y
model = savgol(npoint = 21, deriv = 2, degree = 3)
fit!(model, X) 
Xp = transf(model, X) 
s = Bool.(Y.test)
Xtrain = rmrow(Xp, s)
Ytrain = rmrow(Y, s)
Xtest = Xp[s, :]
Ytest = Y[s, :]

## Below, the reference class is "EEH"
cla1 = "EHH" ; cla2 = "PEE" ; cod = "out"   # here cla2 should be detected
#cla1 = "EHH" ; cla2 = "EHH" ; cod = "in"   # here cla2 should not be detected
s1 = Ytrain.typ .== cla1
s2 = Ytest.typ .== cla2
zXtrain = Xtrain[s1, :]    
zXtest = Xtest[s2, :] 
ntrain = nro(zXtrain)
ntest = nro(zXtest)
ntot = ntrain + ntest
(ntot = ntot, ntrain, ntest)
ytrain = repeat(["in"], ntrain)
ytest = repeat([cod], ntest)

## Group description
model = pcasvd(nlv = 10) 
fit!(model, zXtrain) 
Ttrain = model.fitm.T
Ttest = transf(model, zXtest)
T = vcat(Ttrain, Ttest)
group = vcat(repeat(["1"], ntrain), repeat(["2"], ntest))
i = 1
plotxy(T[:, i], T[:, i + 1], group; leg_title = "Class", xlabel = string("PC", i),  
    ylabel = string("PC", i + 1)).f

#### Occ
model_occ = occstah(; nlv = 5000, scal = true)
fit!(model_occ, zXtrain) 
@names model_occ 
@names model_occ.fitm 
@head model_occ.fitm.V  # random directions 
@head d = model_occ.fitm.d
d = d.dstand
f, ax = plotxy(1:length(d), d; size = (500, 300), xlabel = "Obs. index", 
    ylabel = "Standardized distance")
hlines!(ax, 1; linestyle = :dot)
f

res = predict(model_occ, zXtest) ;
@names res
@head res.d
@head res.pred
tab(res.pred)
errp(res.pred, ytest)
conf(res.pred, ytest).cnt
d1 = model_occ.fitm.d.dstand
d2 = res.d.dstand
d = vcat(d1, d2)
f, ax = plotxy(1:length(d), d, group; size = (500, 300), leg_title = "Class", 
    xlabel = "Obs. index", ylabel = "Standardized distance")
hlines!(ax, 1; linestyle = :dot)
f
```
