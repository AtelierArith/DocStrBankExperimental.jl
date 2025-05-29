A container to enforce an [`AbstractConstraint`](@ref) on a (primitive) value, which may change over time.

The `value` is, optionally controlled through the value of `fatal`, validated upon initial construction, as well as whenever it is mutated.
