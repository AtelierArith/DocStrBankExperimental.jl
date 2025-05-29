```julia
logit(x)

```

The [logit](https://en.wikipedia.org/wiki/Logit) or log-odds transformation, defined as

$$
\operatorname{logit}(x) = \log\left(\frac{x}{1-x}\right)
$$

for $0 < x < 1$.

Its inverse is the [`logistic`](@ref) function.
