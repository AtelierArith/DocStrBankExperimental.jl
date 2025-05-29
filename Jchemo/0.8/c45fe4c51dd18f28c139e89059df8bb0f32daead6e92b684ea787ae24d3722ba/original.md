```
mpar(; kwargs...)
```

Return a tuple with all the combinations of the parameter      values defined in kwargs. Keyword arguments:

  * `kwargs` : Vector(s) of the parameter(s) values.

## Examples

```julia
using Jchemo
nlvdis = 25 ; metric = [:mah] 
h = [1 ; 2 ; Inf] ; k = [500 ; 1000] 
pars = mpar(nlvdis = nlvdis, metric = metric, h = h, k = k) 
length(pars[1])
reduce(hcat, pars)
```
