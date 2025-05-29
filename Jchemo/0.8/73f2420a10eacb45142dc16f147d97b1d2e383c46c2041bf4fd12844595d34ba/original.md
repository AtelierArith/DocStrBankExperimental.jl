```
comdim(; kwargs...)
comdim(Xbl; kwargs...)
comdim(Xbl, weights::Weight; kwargs...)
comdim!(Xbl::Matrix, weights::Weight; kwargs...)
```

Common components and specific weights analysis (CCSWA, a.k.a ComDim).

  * `Xbl` : List of blocks (vector of matrices) of X-data.    Typically, output of function `mblock`.
  * `weights` : Weights (n) of the observations.    Must be of type `Weight` (see e.g. function `mweight`).

Keyword arguments:

  * `nlv` : Nb. global latent variables (LVs = scores) to compute.
  * `bscal` : Type of block scaling. See function `blockscal` for possible values.
  * `tol` : Tolerance value for convergence (Nipals).
  * `maxit` : Maximum number of iterations (Nipals).
  * `scal` : Boolean. If `true`, each column of blocks in `Xbl`    is scaled by its uncorrected standard deviation    (before the block scaling).

"SVD" algorithm of Hannafi & Qannari 2008 p.84.

The function returns several objects, in particular:

  * `T` : The global LVs (not-normed).
  * `U` : The global LVs (normed).
  * `W` : The block weights (normed).
  * `Tb` : The block LVs (in the metric scale), returned **grouped by LV**.
  * `Tbl` : The block LVs (in the original scale), returned **grouped by block**.
  * `Vbl` : The block loadings (normed).
  * `lb` : The block specific weights (saliences) 'lambda'.
  * `mu` : The sum of the block specific weights.

Function `summary` returns: 

  * `explvarx` : Proportion of the total X inertia (squared Frobenious norm)    explained by the global LVs.
  * `explvarxx` : Proportion of the total XX' inertia explained by the global    LVs (= indicator "V" in Qannari et al. 2000, Hanafi et al. 2008).
  * `explxbl` : Proportion of the inertia of each block (= Xbl[k]) explained by the global LVs.
  * `psal2` : Proportion of the squared saliences of each block within each global score.
  * `contrxbl2t` : Contribution of each block to the global LVs (= lb proportions).
  * `rvxbl2t` : RV coefficients between each block and the global LVs.
  * `rdxbl2t` : Rd coefficients between each block and the global LVs.
  * `cortbl2t` : Correlations between the block LVs (= Tbl[k]) and the global LVs.
  * `corx2t` : Correlation between the X-variables and the global LVs.

## References

Cariou, V., Qannari, E.M., Rutledge, D.N., Vigneau, E., 2018.  ComDim: From multiblock data analysis to path modeling. Food  Quality and Preference, Sensometrics 2016: Sensometrics-by-the-Sea  67, 27–34. https://doi.org/10.1016/j.foodqual.2017.02.012

Cariou, V., Jouan-Rimbaud Bouveresse, D., Qannari, E.M.,  Rutledge, D.N., 2019. Chapter 7 - ComDim Methods for the Analysis  of Multiblock Data in a Data Fusion Perspective, in: Cocchi, M. (Ed.),  Data Handling in Science and Technology,  Data Fusion Methodology and Applications. Elsevier, pp. 179–204.  https://doi.org/10.1016/B978-0-444-63984-4.00007-7

Ghaziri, A.E., Cariou, V., Rutledge, D.N., Qannari, E.M., 2016.  Analysis of multiblock datasets using ComDim: Overview and extension  to the analysis of (K + 1) datasets. Journal of Chemometrics 30,  420–429. https://doi.org/10.1002/cem.2810

Hanafi, M., 2008. Nouvelles propriétés de l’analyse en composantes  communes et poids spécifiques. Journal de la société française  de statistique 149, 75–97.

Qannari, E.M., Wakeling, I., Courcoux, P., MacFie, H.J.H., 2000.  Defining the underlying sensory dimensions. Food Quality and  Preference 11, 151–154.  https://doi.org/10.1016/S0950-3293(99)00069-5

## Examples

```julia
using Jchemo, JchemoData, JLD2
mypath = dirname(dirname(pathof(JchemoData)))
db = joinpath(mypath, "data", "ham.jld2") 
@load db dat
@names dat 
X = dat.X
group = dat.group
listbl = [1:11, 12:19, 20:25]
Xbl = mblock(X[1:6, :], listbl)
Xblnew = mblock(X[7:8, :], listbl)
n = nro(Xbl[1]) 

nlv = 3
bscal = :frob
scal = false
#scal = true
model = comdim(; nlv, bscal, scal)
fit!(model, Xbl)
@names model 
@names model.fitm
## Global scores 
@head model.fitm.T
@head transf(model, Xbl)
transf(model, Xblnew)
## Blocks scores
i = 1
@head model.fitm.Tbl[i]
@head transfbl(model, Xbl)[i]

res = summary(model, Xbl) ;
@names res 
res.explvarx
res.explvarxx
res.psal2 
res.contrxbl2t
res.explxbl   # = model.fitm.lb if bscal = :frob
rowsum(Matrix(res.explxbl))
res.rvxbl2t
res.rdxbl2t
res.cortbl2t
res.corx2t 
```
