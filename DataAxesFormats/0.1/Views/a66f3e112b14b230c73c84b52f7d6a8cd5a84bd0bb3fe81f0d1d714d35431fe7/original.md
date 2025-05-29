Specify all the data to expose from a view. We would have liked to specify this as `AbstractVector{<:ViewDatum}` but Julia in its infinite wisdom considers `["a", "b" => "c"]` to be a `Vector{Any}`, which would require literals to be annotated with the type.

!!! note
    [`TensorKey`](@ref)s are interpreted after interpreting all [`MatrixKey`](@ref)s, so they will override them even if they appear earlier in the list of keys. For clarity it is best to list them at the very end of the list.

