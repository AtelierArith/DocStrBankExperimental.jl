```
FitOptions
```

Struct to control fitting.

## Fields

  * `what_fit::Dict{AbstractTransportProperty,Vector{Bool}}`: specify which parameters to fit

## Example

```
FitOptions(;
    what_fit=Dict(
        ThermalConductivity()=>ones(Bool,5), 
        SelfDiffusionCoefficient()=>Bool[0,0,0,1,1])
)
```
