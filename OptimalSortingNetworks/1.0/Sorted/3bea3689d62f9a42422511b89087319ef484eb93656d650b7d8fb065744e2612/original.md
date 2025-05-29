Helper function for making it easy to construct a compare/exchange element for use in [`sorted`](@ref).

Arguments:

1. An optional positional argument, `T`, representing the type of collection that will be sorted.
2. An optional keyword argument, `by`, for specifying the `by` transform. Defaults to `default_minmax_by(T)`, see [`default_minmax_by`](@ref).
3. An optional keyword argument, `less`, for specifying the `less` comparison predicate. Defaults to `default_minmax_less(T)`, see [`default_minmax_less`](@ref).
