```
delete_default!(c::ComponentModel, sym::Symbol)
delete_default!(nw::Network, sni::SymbolicIndex)
```

Removes the `default` value for symbol `sym` in a component model, or for a symbol referenced by `sni` in a network.

See also [`has_default`](@ref), [`set_default!`](@ref).
