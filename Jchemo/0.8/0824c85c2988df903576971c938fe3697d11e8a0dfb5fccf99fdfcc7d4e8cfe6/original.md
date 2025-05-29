```
sampdp(X, k::Int; metric = :eucl)
```

Build training vs. test sets by DUPLEX sampling.  

  * `X` : X-data (n, p).
  * `k` : Nb. pairs (training/test) of observations    to sample. Must be <= n / 2.

Keyword arguments:

  * `metric` : Metric used for the distance computation.   Possible values are: `:eucl` (Euclidean),    `:mah` (Mahalanobis).

Three outputs (= row indexes of the data) are returned: 

  * `train` (`k`),
  * `test` (`k`),
  * `remain` (n - 2 * `k`).

Outputs `train` and `test` are built from the DUPLEX algorithm  (Snee, 1977 p.421). They are expected to cover approximately the same  X-space region and have similar statistical properties. 

In practice, when output `remain` is not empty (i.e. when there  are remaining observations), one common strategy is to add  it to output `train`.

## References

Kennard, R.W., Stone, L.A., 1969. Computer aided design of experiments.  Technometrics, 11(1), 137-148.

Snee, R.D., 1977. Validation of Regression Models: Methods and Examples.  Technometrics 19, 415-428. https://doi.org/10.1080/00401706.1977.10489581

## Examples

```julia
using Jchemo

X = [0.381392  0.00175002 ; 0.1126    0.11263 ; 
    0.613296  0.152485 ; 0.726536  0.762032 ;
    0.367451  0.297398 ; 0.511332  0.320198 ; 
    0.018514  0.350678] 

k = 3
sampdp(X, k)
```
