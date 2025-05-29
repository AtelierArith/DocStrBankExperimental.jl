```
GreaterThanZero()
```

A struct used to intercept when `>=` or `≥` is used in a macro via [`operator_to_set`](@ref).

This struct is not the same as [`Nonnegatives`](@ref) so that we can disambiguate `x >= y` and `x - y in Nonnegatives()`.

This struct is not intended for general usage, but it may be useful to some JuMP extensions.

## Example

```jldoctest
julia> operator_to_set(error, Val(:>=))
GreaterThanZero()
```
