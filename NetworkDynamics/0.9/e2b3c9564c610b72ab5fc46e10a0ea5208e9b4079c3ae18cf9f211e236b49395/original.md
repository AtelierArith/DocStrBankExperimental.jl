```
has_bounds(c::ComponentModel, sym::Symbol)
has_bounds(nw::Network, sni::SymbolicIndex)
```

Checks if a `bounds` value is present for symbol `sym` in a component model, or for a symbol referenced by `sni` in a network.

See also [`get_bounds`](@ref), [`set_bounds!`](@ref).
