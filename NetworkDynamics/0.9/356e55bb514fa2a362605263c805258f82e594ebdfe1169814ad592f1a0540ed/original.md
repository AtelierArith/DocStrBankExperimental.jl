```
get_metadata(c::ComponentModel, sym::Symbol, key::Symbol)
get_metadata(nw::Network, sni::SymbolicIndex, key::Symbol)
```

Retrieves the metadata `key` for symbol `sym` in a component model, or for a symbol referenced by `sni` in a network. Throws an error if the symbol does not exist in the component model.
