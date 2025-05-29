```
delete_metadata!(c::ComponentModel, key::Symbol)
delete_metadata!(nw::Network, idx::Union{VIndex,EIndex}, key::Symbol)
```

Removes the component-wide metadata `key` from the component model, or from a component referenced by `idx` in a network. Returns `true` if the metadata existed and was removed, `false` otherwise.
