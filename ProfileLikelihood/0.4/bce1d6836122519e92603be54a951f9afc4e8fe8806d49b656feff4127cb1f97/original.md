```
struct IrregularGrid{N,B,R,S,T} <: AbstractGrid{N,B,T}
```

Struct for an irregular grid of parameters.

# Fields

  * `lower_bounds::B`: Lower bounds for each parameter.
  * `upper_bounds::B`: Upper bounds for each parameter.
  * `grid::G`: The set of parameter values, e.g. a matrix where each column is the parameter vector.

# Constructor

You can construct a `IrregularGrid` using `IrregularGrid(lower_bounds, upper_bounds, grid)`.
