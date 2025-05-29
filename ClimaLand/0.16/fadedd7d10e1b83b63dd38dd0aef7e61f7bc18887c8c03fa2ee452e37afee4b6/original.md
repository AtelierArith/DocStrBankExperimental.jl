auxiliary_types(m::AbstractModel{FT}) where {FT}

Returns the auxiliary variable types for the model in the form of a tuple.

Types provided must have `ClimaCore.RecursiveApply.rzero(T::DataType)` defined. Common examples  include

  * Float64, Float32 for scalar variables (a scalar value at each

coordinate point)

  * SVector{k,Float64} for a mutable but statically sized array of

length `k` at each coordinate point.

  * Note that Arrays, MVectors are not isbits and cannot be used.

Here, the coordinate points are those returned by coordinates(model).
