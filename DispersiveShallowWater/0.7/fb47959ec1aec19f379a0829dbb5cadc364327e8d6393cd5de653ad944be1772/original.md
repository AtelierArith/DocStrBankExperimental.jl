```
DispersiveShallowWater
```

**DispersiveShallowWater.jl** is a Julia package that implements structure-preserving numerical methods for dispersive shallow water models. It provides provably conservative, entropy-conserving, and well-balanced numerical schemes for some dispersive shallow water models.

The semidiscretizations are based on summation-by-parts (SBP) operators, which are implemented in [SummationByPartsOperators.jl](https://github.com/ranocha/SummationByPartsOperators.jl). To obtain fully discrete schemes, the time integration methods from [OrdinaryDiffEq.jl](https://github.com/SciML/OrdinaryDiffEq.jl) are used to solve the resulting ordinary differential equations. Fully discrete entropy-conservative methods can be obtained by using the relaxation method provided by DispersiveShallowWater.jl.

See also: [DispersiveShallowWater.jl](https://github.com/NumericalMathematics/DispersiveShallowWater.jl)
