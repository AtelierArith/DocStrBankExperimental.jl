```
DensityModel{F} <: AbstractModel
```

`DensityModel` は自己完結型の対数尤度関数 `logdensity` をラップします。

例:

```julia
l(x) = logpdf(Normal(), x)
DensityModel(l)
```
