Specify the data to use for missing properties in a `Daf` data set. This is a dictionary with an [`DataKey`](@ref) specifying for which property we spec,aify a value to, and the value to use. We would have liked to specify this as `AbstractDict{<:DataKey, <:StorageScalarBase}` but Julia in its infinite wisdom considers `Dict(["a" => "b", ("c", "d") => 1])` to be a `Dict{Any, Any}`, which would require literals to be annotated with the type.

!!! note
    A [`TensorKey`](@ref) is interpreted as if it as the set of [`MatrixKey`](@ref)s that are included in the tensor. These are expanded in an internal copy of the dictionary and will override any other specified [`MatrixKey`](@ref).

