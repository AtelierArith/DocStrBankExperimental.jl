```
has_guess(c::ComponentModel, sym::Symbol)
has_guess(nw::Network, sni::SymbolicIndex)
```

Checks if a `guess` value is present for symbol `sym` in a component model, or for a symbol referenced by `sni` in a network.

See also [`get_guess`](@ref), [`set_guess!`](@ref).
