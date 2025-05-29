```
delete_metadata!(c::ComponentModel, sym::Symbol, key::Symbol)
delete_metadata!(nw::Network, sni::SymbolicIndex, key::Symbol)
```

Removes the metadata `key` for symbol `sym` in a component model, or for a symbol referenced by `sni` in a network. Returns `true` if the metadata existed and was removed, `false` otherwise. Throws an error if the symbol does not exist in the component model.
