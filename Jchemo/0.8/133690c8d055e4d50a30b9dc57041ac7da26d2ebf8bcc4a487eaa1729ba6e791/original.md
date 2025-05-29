```
sampwsp(X, dmin; recod = false, maxit = nro(X))
```

Build training vs. test sets by WSP sampling.  

  * `X` : X-data (n, p).
  * `dmin` : Distance "dmin" (Santiago et al. 2012).

Keyword arguments: 

  * `recod` : Boolean indicating if `X` is recoded or not    before the sampling (see below).
  * `maxit` : Maximum number of iterations.

Two outputs (= row indexes of the data) are returned: 

  * `train` (`n` - k),
  * `test` (k).

Output `test` is built from the "Wootton, Sergent, Phan-Tan-Luu" (WSP)  algorithm, assumed to generate samples uniformely distributed in the `X` domain  (Santiago et al. 2012).

If `recod = true`, each column x of `X` is recoded within [0, 1] and the center of  the domain is the vector `repeat([.5], p)`. Column x is recoded such as: 

  * vmin = minimum(x)
  * vmax = maximum(x)
  * vdiff = vmax - vmin
  * x .=  0.5 .+ (x .- (vdiff / 2 + vmin)) / vdiff

## References

Béal A. 2015. Description et sélection de données en grande dimensio. Thèse de doctorat. Laboratoire d’Instrumentation et de sciences analytiques, Ecole doctorale des siences chimiques, Université d'Aix-Marseille.

Santiago, J., Claeys-Bruno, M., Sergent, M., 2012. Construction of space-filling  designs using WSP algorithm for high dimensional spaces.  Chemometrics and Intelligent Laboratory Systems, Selected Papers from  Chimiométrie 2010 113, 26–31. https://doi.org/10.1016/j.chemolab.2011.06.003

## Examples

```julia
using Jchemo

n = 600 ; p = 2
X = rand(n, p)
dmin = .5
s = sampwsp(X, dmin)
@names res
@show length(s.test)
plotxy(X[s.test, 1], X[s.test, 2]).f
```
