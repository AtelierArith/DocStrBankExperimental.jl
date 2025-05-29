```
has_init(c::ComponentModel, sym::Symbol)
has_init(nw::Network, sni::SymbolicIndex)
```

Checks if a `init` value is present for symbol `sym` in a component model, or for a symbol referenced by `sni` in a network.

See also [`get_init`](@ref), [`set_init!`](@ref).
