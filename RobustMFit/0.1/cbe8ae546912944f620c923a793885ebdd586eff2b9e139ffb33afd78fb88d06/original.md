```
Tukey(kL::Real, kU::Real) <: TukeySetting
Tukey(k::Real) <: TukeySetting
```

Data type for function selection in M-estimation using Tukey's functions. `kL` and `kU` give lower and upper tuning constants respectively. If only one tuning constant provided, symmetric functions are assumed.

# Example

```julia
Tukey(4.5, 6)
Tukey(4.5)
```
