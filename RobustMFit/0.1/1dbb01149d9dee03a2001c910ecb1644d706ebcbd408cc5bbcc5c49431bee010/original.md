```
HampelS(kL::Vector{Real}, kU::Vector{Real}, ϵ::Real) <: HampelSetting
```

Data type for function selection in M-estimation using smoothed versions of Hampel's functions. `kL` and `kU` give lower and upper tuning constants (vectors) respectively. If only one tuning constant vector provided, symmetric functions are assumed. Smoothing is carried out by Log-Exp-Smoothing, see [Xia (2019)](https://doi.org/10.1007/s10825-019-01356-w)

# Example

```julia
HampelS([1, 2, 5], [1, 4, 7], 0.1)
Hampel([1, 2, 5], [1, 4, 7], ϵ = 0.1)
Hampel([1, 2, 5], ϵ = 0.1)
```
