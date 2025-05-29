```
delete_bounds!(c::ComponentModel, sym::Symbol)
delete_bounds!(nw::Network, sni::SymbolicIndex)
```

Removes the `bounds` value for symbol `sym` in a component model, or for a symbol referenced by `sni` in a network.

See also [`has_bounds`](@ref), [`set_bounds!`](@ref).
