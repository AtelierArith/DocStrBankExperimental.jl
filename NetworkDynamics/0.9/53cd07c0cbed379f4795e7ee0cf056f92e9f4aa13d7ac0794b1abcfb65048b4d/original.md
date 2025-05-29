```
set_guess!(c::ComponentModel, sym::Symbol, value)
set_guess!(nw::Network, sni::SymbolicIndex, value)
```

Sets the `guess` value for symbol `sym` to `value` in a component model, or for a symbol referenced by `sni` in a network.

See also [`has_guess`](@ref), [`get_guess`](@ref).
