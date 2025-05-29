```
struct DataMatrix{T,Tv,To}
```

A `DataMatrix` represents a matrix together with annotations for variables and observations.

Fields:

  * `matrix::T` - The matrix.
  * `var::Tv` - Variable annotations.
  * `obs::To` - Observation annotations.
  * `models::Vector{ProjectionModel}` - Models used in the creation of this `DataMatrix`.

The first column of the `var` and `obs` tables should contain unique IDs.
