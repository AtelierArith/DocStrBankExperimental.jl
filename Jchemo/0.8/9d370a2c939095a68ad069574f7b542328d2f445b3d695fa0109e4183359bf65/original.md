```
samprand(n::Int, k::Int; replace = false)
```

Build training vs. test sets by random sampling.  

  * `n` : Total nb. of observations.
  * `k` : Nb. test observations to sample.

Keyword arguments:

  * `replace` : Boolean. If `false`, the sampling is    without replacement.

Two outputs are returned (= row indexes of the data): 

  * `train` (`n` - `k`),
  * `test` (`k`).

Output `test` is built by random sampling within `1:n`. 

## Examples

```julia
using Jchemo

n = 10
samprand(n, 4)
```
