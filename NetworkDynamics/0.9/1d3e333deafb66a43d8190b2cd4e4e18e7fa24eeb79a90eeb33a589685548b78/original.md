```
get_bounds(c::ComponentModel, sym::Symbol)
get_bounds(nw::Network, sni::SymbolicIndex)
```

Returns the `bounds` value for symbol `sym` in a component model, or for a symbol referenced by `sni` in a network.

See also [`has_bounds`](@ref), [`set_bounds!`](@ref).
