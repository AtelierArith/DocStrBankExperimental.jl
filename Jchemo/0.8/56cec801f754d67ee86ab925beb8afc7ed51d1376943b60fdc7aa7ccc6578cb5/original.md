```
rv(X, Y; centr = true)
rv(Xbl::Vector; centr = true)
```

Compute RV coefficients.

  * `X` : Matrix (n, p).
  * `Y` : Matrix (n, q).
  * `Xbl` : A list (vector) of matrices.
  * `centr` : Boolean indicating if the matrices    will be internally centered or not.

RV is bounded within [0, 1]. 

A dissimilarty measure between `X` and `Y` can be computed by d = sqrt(2 * (1 - RV)).

## References

Escoufier, Y., 1973. Le Traitement des Variables Vectorielles.  Biometrics 29, 751–760. https://doi.org/10.2307/2529140

Josse, J., Holmes, S., 2016. Measuring multivariate association and beyond.  Stat Surv 10, 132–167. https://doi.org/10.1214/16-SS116

Josse, J., Pagès, J., Husson, F., 2008. Testing the significance of  the RV coefficient. Computational Statistics & Data Analysis 53, 82–91.  https://doi.org/10.1016/j.csda.2008.06.012

Kazi-Aoual, F., Hitier, S., Sabatier, R., Lebreton, J.-D., 1995.  Refined approximations to permutation tests for multivariate inference.  Computational Statistics & Data Analysis 20, 643–656.  https://doi.org/10.1016/0167-9473(94)00064-2

Mayer, C.-D., Lorent, J., Horgan, G.W., 2011. Exploratory Analysis  of Multiple Omics Datasets Using the Adjusted RV Coefficient. Statistical  Applications in Genetics and Molecular Biology 10. https://doi.org/10.2202/1544-6115.1540

Smilde, A.K., Kiers, H.A.L., Bijlsma, S., Rubingh, C.M., van Erk, M.J., 2009.  Matrix correlations for high-dimensional data: the modified RV-coefficient.  Bioinformatics 25, 401–405. https://doi.org/10.1093/bioinformatics/btn634

Robert, P., Escoufier, Y., 1976. A Unifying Tool for Linear Multivariate  Statistical Methods: The RV-Coefficient. Journal of the Royal Statistical Society:  Series C (Applied Statistics) 25, 257–265. https://doi.org/10.2307/2347233

## Examples

```julia
using Jchemo
X = rand(5, 10)
Y = rand(5, 3)
rv(X, Y)

X = rand(5, 15) 
listbl = [3:4, 1, [6; 8:10]]
Xbl = mblock(X, listbl)
rv(Xbl)
```
