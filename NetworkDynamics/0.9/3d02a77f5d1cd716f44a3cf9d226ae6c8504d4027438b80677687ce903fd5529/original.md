```
has_default(c::ComponentModel, sym::Symbol)
has_default(nw::Network, sni::SymbolicIndex)
```

Checks if a `default` value is present for symbol `sym` in a component model, or for a symbol referenced by `sni` in a network.

See also [`get_default`](@ref), [`set_default!`](@ref).
