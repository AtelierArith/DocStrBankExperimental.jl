```
Andrew(kL::Real, kU::Real) <: AndrewSetting
Andrew(k::Real) <: AndrewSetting
```

Data type for function selection in M-estimation using Andrew's wave functions. `kL` and `kU` give lower and upper tuning constants respectively. If only one tuning constant provided, symmetric functions are assumed.

# Example

```julia
Andrew(4.5, 6)
Andrew(4.5)
```
