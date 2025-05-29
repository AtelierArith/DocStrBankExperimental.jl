prognostic_types(m::AbstractModel{FT}) where {FT}

Returns the prognostic variable types for the model in the form of a tuple.

Types provided must have `ClimaCore.RecursiveApply.rzero(T::DataType)`  defined. Common examples  include

  * Float64, Float32 for scalar variables (a scalar value at each

coordinate point)

  * SVector{k,Float64} for a mutable but statically sized array of

length `k` at each coordinate point.

Here, the coordinate points are those returned by coordinates(model).

Note that this default suggests that a model has no prognostic variables, which is an invalid model setup. This function is meant to be extended for all models.
