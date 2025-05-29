```
get_initial_state(c::ComponentModel, syms; missing_val=nothing)
get_initial_state(nw::Network, sni::SymbolicIndex; missing_val=nothing)
```

Returns the initial state for symbol `sym` (single symbol or vector) of the component model `c`. Returns `missing_val` if the symbol is not initialized. Also works for observed symbols.

See also: [`dump_initial_state`](@ref).
