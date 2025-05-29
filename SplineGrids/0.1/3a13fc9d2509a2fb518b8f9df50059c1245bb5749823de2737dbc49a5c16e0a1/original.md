```
SplineDimension(
    n_basis_functions::Integer,
    degree::Integer,
    n_sample_points::Integer;
    max_derivative_order::Integer = 0,
    knot_vector::Union{Nothing, KnotVector{Tv, Ti}} = nothing,
    backend::Backend = CPU(),
    float_type::Type{Tv} = Float32,
    int_type::Type{Ti} = Int32,
    kwargs...)::SplineDimension where {Tv <: AbstractFloat, Ti <: Integer}
```

Constructor for a SplineDimension. Optionally a `knot_vector` kwarg can be passed, otherwise a default knot vector is generated. For now by default the sample points are evenly spaced on the extent of the knot vector. Key word arguments are passed to the KnotVector constructor.

## Inputs

  * `n_basis_functions`: The number of basis functions of this spline dimension
  * `degree`: The degree of the basis functions of this spline dimension
  * `n_sample_points`: The number of points at which the domain of the basis functions will be sampled
  * `max_derivative_order`: The maximum derivative order of the basis functions that will be computed in `evaluate!`. Defaults to `0`. `knot_vector`: A knot vector on which the basis functions will be defined. Defaults to `nothing`, which means that a default clamped/open equally spaced knot vector will be defined.
  * `backend`: The KernelAbstractions backend of the arrays in the object. Defaults to `CPU()`. NOTE: If a knot vector is supplied, its backend takes precedence.
  * `float_type`: The type of all floating point arrays. Defaults to `Float32`.
