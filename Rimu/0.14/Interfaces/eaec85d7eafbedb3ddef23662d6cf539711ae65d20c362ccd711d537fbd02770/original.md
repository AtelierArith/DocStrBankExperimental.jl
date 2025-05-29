```
allows_address_type(operator, addr_or_type)
```

Returns `true` if `addr_or_type` is a valid address for `operator`. Otherwise, returns `false`.

Part of the [`AbstractHamiltonian`](@ref) interface.

# Extended help

Defaults to `addr_or_type <: typeof(starting_address(operator))`. Overload this function if the operator can be used with addresses of different types.
