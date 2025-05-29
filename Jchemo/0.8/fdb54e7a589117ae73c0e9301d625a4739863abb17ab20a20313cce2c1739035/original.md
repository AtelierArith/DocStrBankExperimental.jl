```
mbpca(; kwargs...)
mbpca(Xbl; kwargs...)
mbpca(Xbl, weights::Weight; kwargs...)
mbpca!(Xbl::Matrix, weights::Weight; kwargs...)
```

Consensus principal components analysis (CPCA, a.k.a MBPCA).

  * `Xbl` : List of blocks (vector of matrices) of X-data.    Typically, output of function `mblock`.
  * `weights` : Weights (n) of the observations.    Must be of type `Weight` (see e.g. function `mweight`).

Keyword arguments:

  * `nlv` : Nb. global latent variables (LVs = scores) to compute.
  * `bscal` : Type of block scaling. See function `blockscal` for possible values.
  * `tol` : Tolerance value for Nipals convergence.
  * `maxit` : Maximum number of iterations (Nipals).
  * `scal` : Boolean. If `true`, each column of blocks in `Xbl`    is scaled by its uncorrected standard deviation (before the block scaling).

CPCA algorithm (Westerhuis et a; 1998), a.k.a MBPCA, and reffered to as CPCA-W in  Smilde et al. 2003. 

Apart eventual block scaling, the MBPCA is equivalent to the PCA of the  horizontally concatenated matrix X = [X1 X2 ... Xk](SUM-PCA in Smilde et al 2003).

The function returns several objects, in particular:

  * `T` : The global LVs (not-normed).
  * `U` : The global LVs (normed).
  * `W` : The block weights (normed).
  * `Tb` : The block LVs (in the metric scale), returned **grouped by LV**.
  * `Tbl` : The block LVs (in the original scale), returned **grouped by block**.
  * `Vbl` : The block loadings (normed).
  * `lb` : The block specific weights ('lambda') for the global LVs.
  * `mu` : The sum of the block specific weights (= eigen values of the global PCA).

Function `summary` returns: 

  * `explvarx` : Proportion of the total X inertia (squared Frobenious norm)    explained by the global LVs.
  * `explxbl` : Proportion of the inertia of each block (= Xbl[k]) explained by the global LVs.
  * `contrxbl2t` : Contribution of each block to the global LVs (= lb proportions).
  * `rvxbl2t` : RV coefficients between each block and the global LVs.
  * `rdxbl2t` : Rd coefficients between each block and the global LVs.
  * `cortbl2t` : Correlations between the block LVs (= Tbl[k]) and the global LVs.
  * `corx2t` : Correlation between the X-variables and the global LVs.

## References

Mangamana, E.T., Cariou, V., Vigneau, E., Glèlè Kakaï, R.L.,  Qannari, E.M., 2019. Unsupervised multiblock data  analysis: A unified approach and extensions. Chemometrics and  Intelligent Laboratory Systems 194, 103856.  https://doi.org/10.1016/j.chemolab.2019.103856

Smilde, A.K., Westerhuis, J.A., de Jong, S., 2003. A framework for sequential  multiblock component methods. Journal of Chemometrics 17, 323–337.  https://doi.org/10.1002/cem.811

Westerhuis, J.A., Kourti, T., MacGregor, J.F., 1998. Analysis  of multiblock and hierarchical PCA and PLS models. Journal  of Chemometrics 12, 301–321.  https://doi.org/10.1002/(SICI)1099-128X(199809/10)12:5<301::AID-CEM515>3.0.CO;2-S

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
model = mbpca(; nlv, bscal, scal)
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
res.explxbl   # = model.fitm.lb if bscal = :frob
rowsum(Matrix(res.explxbl))
res.contrxbl2t
res.rvxbl2t
res.rdxbl2t
res.cortbl2t
res.corx2t 
```
