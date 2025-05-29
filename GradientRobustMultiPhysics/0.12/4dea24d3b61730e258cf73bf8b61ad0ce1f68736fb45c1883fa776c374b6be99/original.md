```julia
DataFunction(
    kernel::Function,
    argsizes;
    Tv,
    Ti,
    dependencies,
    bonus_quadorder,
    name
) -> GradientRobustMultiPhysics.DataFunction{Float64, Int32, _A, _B, _C, _D, _E, <:Function} where {_A, _B, _C, _D, _E}

```

generates a DataFunction that can be used in the construction of PDEoperators, interpolations etc. and essentially consists of a kernel function specified by the user plus additional information on argument dimensions and additional dependencies:

  * kernel   : Function with interface (result, ...)
  * argsizes : expected lengths of [result, interface]

Optional arguments:

  * dependencies    : substring of "XTIL" that specifies if the kernel also depends on space coordinates (X), time (T), item (I), local coordinates (L)
  * bonus_quadorder : is added to the quadrature order computed based on the used FESpaces during assembly
  * name            : name of this Action used in print messages
  * Tv              : expected NumberType for result/input
  * Ti              : expected NumberType for grid enumeration infos (e.g. item/region numbers when "I" dependecy is used)
