```
blockscal(; kwargs...)
blockscal(Xbl; kwargs...)
blockscal(Xbl, weights::Weight; kwargs...)
```

Scale multiblock X-data.

  * `Xbl` : List of blocks (vector of matrices) of X-data    Typically, output of function `mblock` from (n, p) data.
  * `weights` : Weights (n) of the observations (rows    of the blocks). Must be of type `Weight` (see e.g.    function `mweight`).

Keyword arguments:

  * `centr` : Boolean. If `true`, each column of blocks in `Xbl`    is centered (before the block scaling).
  * `scal` : Boolean. If `true`, each column of blocks in `Xbl`    is scaled by its uncorrected standard deviation    (before the block scaling).
  * `bscal` : Type of block scaling. Possible values are:   `:none`, `:frob`, `:mfa`, `:ncol`, `:sd`. See thereafter.

If implemented, the data transformations follow the order: column centering, column scaling  and finally block scaling. 

Types of block scaling:

  * `:none` : No block scaling.
  * `:frob` : Let D be the diagonal matrix of vector `weights.w`.    Each block X is divided by its Frobenius norm  = sqrt(tr(X' * D * X)).    After this scaling, tr(X' * D * X) = 1.
  * `:mfa` : Each block X is divided by sv, where sv is the dominant singular    value of X (this is the "MFA" approach; "AFM "in French).
  * `:ncol` : Each block X is divided by the nb. of columns of the block.
  * `:sd` : Each block X is divided by sqrt(sum(weighted variances of the block-columns)).    After this scaling, sum(weighted variances of the block-columns) = 1.

## Examples

```julia
using Jchemo
n = 5 ; m = 3 ; p = 10 
X = rand(n, p) 
Xnew = rand(m, p)
listbl = [3:4, 1, [6; 8:10]]
Xbl = mblock(X, listbl) 
Xblnew = mblock(Xnew, listbl) 
@head Xbl[3]

centr = true ; scal = true
bscal = :frob
model = blockscal(; centr, scal, bscal)
fit!(model, Xbl)
## Data transformation
zXbl = transf(model, Xbl) ; 
@head zXbl[3]

zXblnew = transf(model, Xblnew) ; 
zXblnew[3]
```
