```
recod_indbylev(x::Union{Int, Array{Int}}, lev::Array)
```

Recode an index variable to levels.

  * `x` : Index variable (n) to replace.
  * `lev` : Vector containing the categorical levels.

Assuming slev = 'sort(unique(lev))', each element `x[i]` (i = 1, ..., n) is  replaced by `slev[x[i]]`, see examples.

*Warning*: Vector `x` must contain integers between 1 and nlev, where nlev is the number of levels in `lev`. 

## Examples

```julia
using Jchemo

x = [2 ; 1 ; 2 ; 2]
lev = ["B" ; "C" ; "AA" ; "AA"]
mlev(x)
mlev(lev)
[x recod_indbylev(x, lev)]
recod_indbylev([2], lev)
recod_indbylev(2, lev)

x = [2 ; 1 ; 2]
lev = [3 ; 0 ; 0 ; -1]
mlev(x)
mlev(lev)
recod_indbylev(x, lev)
```
