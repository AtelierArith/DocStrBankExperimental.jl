```
UNIFACModel <: ActivityModel

UNIFAC2(components;
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
  * `B`: Pair Parameter (`Float64`, asymetrical, defaults to `0`) - Binary group Interaction Energy Parameter
  * `C`: Pair Parameter (`Float64`, asymetrical, defaults to `0`) - Binary group Interaction Energy Parameter

## Input models

  * `puremodel`: model to calculate pure pressure-dependent properties

## Description

UNIFAC 2.0 activity model. Modified UNIFAC 2.0 (Dortmund) implementation. The method is identical to [`UNIFAC`](@ref) but with a new parameters fitted by matrix completion methods.

## References

1. Hayer, N., Hasse, H., Jirasek, F., Modified UNIFAC 2.0 - A Group-Contribution Method Completed with Machine Learning. Arxive preprint (2024). [10.48550/arXiv.2412.12962](https://doi.org/10.48550/arXiv.2412.12962)

).
