```
Huber(kL::Real, kU::Real) <: HuberSetting
Huber(k::Real) <: HuberSetting
```

Data type for function selection in M-estimation using Huber's functions. `kL` and `kU` give lower and upper tuning constants respectively. If only one tuning constant provided, symmetric functions are assumed.

# Example

```julia
Huber(1.5, 2)
Huber(1.5)
```
