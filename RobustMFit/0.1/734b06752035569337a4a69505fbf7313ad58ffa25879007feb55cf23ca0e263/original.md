```
AndrewS(kL::Real, kU::Real, ϵ::Real) <: AndrewSetting
```

Data type for function selection in M-estimation using smoothed versions of Andrew's wave functions. `kL` and `kU` give lower and upper tuning constants respectively. If only one tuning constant provided, symmetric functions are assumed. Smoothing is carried out by Log-Exp-Smoothing, see [Xia (2019)](https://doi.org/10.1007/s10825-019-01356-w)

# Example

```julia
AndrewS(4.5, 6, 0.1)
Andrew(4.5, 6, ϵ = 0.1)
Andrew(4.5, ϵ = 0.1)
```
