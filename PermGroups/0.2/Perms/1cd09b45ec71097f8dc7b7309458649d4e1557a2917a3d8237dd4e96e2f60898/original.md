`Perm{T}(x::Integer...)where T<:Integer`

returns  a cycle.  For example  `Perm{Int8}(1,2,3)` constructs the cycle `(1,2,3)` as a `Perm{Int8}`. If omitted `{T}` is taken to be `{Int16}`.
