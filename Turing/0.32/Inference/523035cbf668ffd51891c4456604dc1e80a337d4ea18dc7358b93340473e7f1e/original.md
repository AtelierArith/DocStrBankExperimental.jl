```
IS()
```

Importance sampling algorithm.

Usage:

```julia
IS()
```

Example:

```julia
# Define a simple Normal model with unknown mean and variance.
@model function gdemo(x)
    s² ~ InverseGamma(2,3)
    m ~ Normal(0,sqrt.(s))
    x[1] ~ Normal(m, sqrt.(s))
    x[2] ~ Normal(m, sqrt.(s))
    return s², m
end

sample(gdemo([1.5, 2]), IS(), 1000)
```
