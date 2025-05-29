```
sampsys(y, k::Int)
```

Build training vs. test sets by systematic sampling      over a quantitative variable.  

  * `y` : Quantitative variable (n) to sample.
  * `k` : Nb. test observations to sample.    Must be >= 2.

Two outputs are returned (= row indexes of the data): 

  * `train` (n - `k`),
  * `test` (`k`).

Output `test` is built by systematic sampling over the rank of  the `y` observations. For instance if `k` / n ~ .3, one observation  over three observations over the sorted `y` is selected. 

Output `test` always contains the indexes of the minimum and  maximum of `y`.

## Examples

```julia
using Jchemo 

y = rand(7)
[y sort(y)]
res = sampsys(y, 3)
sort(y[res.test])
```
