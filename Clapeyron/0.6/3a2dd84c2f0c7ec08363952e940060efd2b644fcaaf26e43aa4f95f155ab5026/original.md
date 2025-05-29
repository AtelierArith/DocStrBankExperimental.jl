```
ogUNIFACModel <: UNIFACModel

ogUNIFAC2(components;
puremodel = PR, 
userlocations = String[],
group_userlocations = String[],
pure_userlocations = String[],
verbose = false,
reference_state = nothing)
```

## Input parameters

  * `R`: Single Parameter (`Float64`)  - Normalized group Van der Vals volume
  * `Q`: Single Parameter (`Float64`) - Normalized group Surface Area
  * `A`: Pair Parameter (`Float64`, asymetrical, defaults to `0`) - Binary group Interaction Energy Parameter

## Input models

  * `puremodel`: model to calculate pure pressure-dependent properties

UNIFAC 2.0 (UNIQUAC Functional-group Activity Coefficients) activity model. Original formulation. The method is identical to [`ogUNIFAC`](@ref) but with a new parameters fitted by matrix completion methods.

## References

1. Hayer, N., Wendel, T., Mandt, S., Hasse, H., Jirasek, F., Advancing Thermodynamic Group-Contribution Methods by Machine Learning: UNIFAC 2.0, Chemical Engineering Journal 504 (2025) 158667. [10.1016/j.cej.2024.158667](https://doi.org/10.1016/j.cej.2024.158667).
