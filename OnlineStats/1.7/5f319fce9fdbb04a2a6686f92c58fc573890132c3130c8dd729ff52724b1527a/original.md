```
FitGamma(; weight)
```

Online parameter estimate of a Gamma distribution (Method of Moments).

# Example

```
using Random
o = fit!(FitGamma(), randexp(10^5))
```
