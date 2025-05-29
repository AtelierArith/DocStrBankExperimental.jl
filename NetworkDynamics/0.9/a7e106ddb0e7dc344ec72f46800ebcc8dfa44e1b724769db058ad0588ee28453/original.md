```
delete_init!(c::ComponentModel, sym::Symbol)
delete_init!(nw::Network, sni::SymbolicIndex)
```

Removes the `init` value for symbol `sym` in a component model, or for a symbol referenced by `sni` in a network.

See also [`has_init`](@ref), [`set_init!`](@ref).
