```
getdist(x)
```

Get the probability distribution associated with symbolic variable `x`. If no distribution is associated with `x`, `nothing` is returned. Create parameters with associated distributions like this

```julia
using Distributions
d = Normal(0, 1)
@parameters u [dist = d]
hasdist(u) # true
getdist(u) # retrieve distribution
```
