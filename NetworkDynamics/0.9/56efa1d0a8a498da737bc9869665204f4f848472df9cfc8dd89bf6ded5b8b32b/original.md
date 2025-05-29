```
set_default!(c::ComponentModel, sym::Symbol, value)
set_default!(nw::Network, sni::SymbolicIndex, value)
```

Sets the `default` value for symbol `sym` to `value` in a component model, or for a symbol referenced by `sni` in a network.

See also [`has_default`](@ref), [`get_default`](@ref).
