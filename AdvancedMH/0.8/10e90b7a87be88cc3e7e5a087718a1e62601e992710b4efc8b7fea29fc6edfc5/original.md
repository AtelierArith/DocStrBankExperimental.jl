```
DensityModel{F} <: AbstractModel
```

`DensityModel` wraps around a self-contained log-liklihood function `logdensity`.

Example:

```julia
l(x) = logpdf(Normal(), x)
DensityModel(l)
```
