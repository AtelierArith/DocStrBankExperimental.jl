```
set_init!(c::ComponentModel, sym::Symbol, value)
set_init!(nw::Network, sni::SymbolicIndex, value)
```

Sets the `init` value for symbol `sym` to `value` in a component model, or for a symbol referenced by `sni` in a network.

See also [`has_init`](@ref), [`get_init`](@ref).
