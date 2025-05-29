```
conf(pred, y; digits = 1)
```

Confusion matrix.

  * `pred` : Univariate predictions.
  * `y` : Univariate observed data.

Keyword arguments:

  * `digits` : Nb. digits used to round percentages.

## Examples

```julia
using Jchemo, CairoMakie

y = ["d"; "c"; "b"; "c"; "a"; "d"; "b"; "d"; 
    "b"; "b"; "a"; "a"; "c"; "d"; "d"]
pred = ["a"; "d"; "b"; "d"; "b"; "d"; "b"; "d"; 
    "b"; "b"; "a"; "a"; "d"; "d"; "d"]
#y = rand(1:10, 200); pred = rand(1:10, 200)

res = conf(pred, y) ;
@names res
res.cnt       # Counts (dataframe built from `A`) 
res.pct       # Row %  (dataframe built from `Apct`))
res.A         
res.Apct
res.diagpct
res.accpct    # Accuracy (% classification successes)
res.lev       # Levels

plotconf(res).f

plotconf(res; cnt = false, ptext = false).f
```
