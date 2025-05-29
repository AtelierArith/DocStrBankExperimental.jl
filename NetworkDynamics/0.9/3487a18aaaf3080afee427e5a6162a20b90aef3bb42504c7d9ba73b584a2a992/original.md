```
set_bounds!(c::ComponentModel, sym::Symbol, value)
set_bounds!(nw::Network, sni::SymbolicIndex, value)
```

Sets the `bounds` value for symbol `sym` to `value` in a component model, or for a symbol referenced by `sni` in a network.

See also [`has_bounds`](@ref), [`get_bounds`](@ref).
