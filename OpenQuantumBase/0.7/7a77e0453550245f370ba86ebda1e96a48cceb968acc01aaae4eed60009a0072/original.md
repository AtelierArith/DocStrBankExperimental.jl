```julia
struct CustomCouplings <: OpenQuantumBase.AbstractTimeDependentCouplings
```

`CustomCouplings` is a container for any user defined coupling operators.

# Fields

  * `coupling`: A 1-D array of callable objects that returns coupling matrices
  * `size`: Size of the coupling operator
