```
has_metadata(c::ComponentModel, sym::Symbol, key::Symbol)
has_metadata(nw::Network, sni::SymbolicIndex, key::Symbol)
```

Checks if symbol metadata `key` is present for symbol `sym` in a component model, or for a symbol referenced by `sni` in a network. Throws an error if the symbol does not exist in the component model.
