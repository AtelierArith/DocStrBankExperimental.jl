```
get_guess(c::ComponentModel, sym::Symbol)
get_guess(nw::Network, sni::SymbolicIndex)
```

Returns the `guess` value for symbol `sym` in a component model, or for a symbol referenced by `sni` in a network.

See also [`has_guess`](@ref), [`set_guess!`](@ref).
