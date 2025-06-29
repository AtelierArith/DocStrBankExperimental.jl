```
vip(object::Union{Plsr, Pcr, Splsr, Spcr}; nlv = nothing)
vip(object::Union{Plsr, Pcr, Splsr, Spcr}, Y; nlv = nothing)
```

Variable importance on Projections (VIP).

  * `object` : The fitted model.
  * `Y` : The Y-data that was used to fit the model.

Keyword arguments:

  * `nlv` : Nb. latent variables (LVs) to consider.   If `nothing`, the maximal model is considered.

For a PLS model  (or PCR, etc.) fitted on (X, Y) with a number  of A latent variables, and for variable xj (column j of X): 

  * VIP(xj) = Sum.a(1,...,A) R2(Yc, ta) waj^2 / Sum.a(1,...,A) R2(Yc, ta) (1 / p)

where:

  * Yc is the centered Y,
  * ta is the a-th X-score,
  * R2(Yc, ta) is the proportion of Yc-variance explained    by ta, i.e. ||Yc.hat||^2 / ||Yc||^2 (where Yc.hat is the    LS estimate of Yc by ta).

When `Y` is used, R2(Yc, ta) is replaced by the redundancy Rd(Yc, ta) (see function `rd`), such as in Tenenhaus 1998 p.139. 

## References

Chong, I.-G., Jun, C.-H., 2005. Performance of some variable selection  methods when multicollinearity is present. Chemometrics and Intelligent  Laboratory Systems 78, 103–112. https://doi.org/10.1016/j.chemolab.2004.12.011

Mehmood, T., Sæbø, S., Liland, K.H., 2020. Comparison of variable  selection methods in partial least squares regression. Journal of  Chemometrics 34, e3226. https://doi.org/10.1002/cem.3226

Tenenhaus, M., 1998. La régression PLS: théorie et pratique.  Editions Technip, Paris.

## Examples

```julia
using Jchemo

X = [1. 2 3 4; 4 1 6 7; 12 5 6 13; 27 18 7 6 ; 12 11 28 7] 
Y = [10. 11 13; 120 131 27; 8 12 4; 1 200 8; 100 10 89] 
y = Y[:, 1] 
ycla = [1; 1; 1; 2; 2]

nlv = 3
model = plskern(; nlv)
fit!(model, X, y)
res = vip(model.fitm)
@names res
res.imp

fit!(model, X, Y)
vip(model.fitm).imp
vip(model.fitm, Y).imp

## For PLSDA

model = plsrda(; nlv) 
fit!(model, X, ycla)
@names model.fitm
fitm = model.fitm.fitm ;  # fitted PLS model
vip(fitm).imp
Ydummy = dummy(ycla).Y
vip(fitm, Ydummy).imp

model = plslda(; nlv) 
fit!(model, X, ycla)
@names model.fitm.fitm
fitm = model.fitm.fitm.embfitm ;  # fitted PLS model
vip(fitm).imp
vip(fitm, Ydummy).imp
```
