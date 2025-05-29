```
Hampel(kL::Vector{Real}, kU::Vector{Real}) <: HampelSetting
Hampel(k::Vector{Real}) <: HampelSetting
```

Data type for function selection in M-estimation using Hampel's functions. `kL` and `kU` give lower and upper tuning constants (vectors) respectively. If only one tuning constant vector provided, symmetric functions are assumed.

# Example

```julia
Hampel([1, 2, 5], [1, 4, 7])
Hampel([1, 2, 5])
```
