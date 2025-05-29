```
struct SymbolCache
function SymbolCache(vars, [params, [indepvars]]; defaults = Dict(), timeseries_parameters = nothing)
```

A struct implementing the index provider interface for a collection of variables, parameters, and independent variables. `vars` and `params` can be specified as arrays (in which case the index of a symbol is its index in the array) or `AbstractDict`s mapping symbols to indices. It is considered time dependent if it contains at least one independent variable.

It returns `true` for `is_observed(::SymbolCache, sym)` if `sym isa Union{Expr, Array{Expr}, Tuple{Vararg{Expr}}`. Functions can be generated using `observed` for `Expr`s involving variables in the `SymbolCache` if it has at most one independent variable.

`defaults` is an `AbstractDict` mapping variables and/or parameters to their default initial values. The default initial values can also be other variables/ parameters or expressions of them. `timeseries_parameters` is an `AbstractDict` the timeseries parameters in `params` to their [`ParameterTimeseriesIndex`](@ref) indexes.

The independent variable may be specified as a single symbolic variable instead of an array containing a single variable if the system has only one independent variable.
