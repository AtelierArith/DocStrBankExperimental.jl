get*type*parameters(type*or*obj, [pos])

Return a tuple containing the type parameters of a given type or object. Optionally you can specify a position to just get the parameter for that position, or a tuple of positions to get a subset of parameters.

If parameters are unspecified, returns a `TypeVar`. For a checked version, see [`type_parameters`](@ref).
