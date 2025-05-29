```
set_metadata!(c::ComponentModel, sym::Symbol, key::Symbol, value)
set_metadata!(nw::Network, sni::SymbolicIndex, key::Symbol, value)
set_metadata!(c::ComponentModel, sym::Symbol, pair::Pair)
set_metadata!(nw::Network, sni::SymbolicIndex, pair::Pair)
```

Sets the metadata `key` for symbol `sym` to `value` in a component model, or for a symbol referenced by `sni` in a network. Throws an error if the symbol does not exist in the component model.
