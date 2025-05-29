```julia
mutable struct LinearizationProblem{F<:ModelingToolkit.LinearizationFunction, T}
```

A struct representing a linearization operation to be performed. Can be symbolically indexed to efficiently update the operating point for multiple linearizations in a loop. The value of the independent variable can be set by mutating the `.t` field of this struct.
