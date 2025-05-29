type*parameters(type*or_obj, [pos])

Return a tuple containing the type parameters of a given type or object. Optionally you can specify a position to just get the parameter for that position, or a tuple of positions to get a subset of parameters.

Errors if parameters are unspecified. For an unchecked version, see [`get_type_parameters`](@ref).
