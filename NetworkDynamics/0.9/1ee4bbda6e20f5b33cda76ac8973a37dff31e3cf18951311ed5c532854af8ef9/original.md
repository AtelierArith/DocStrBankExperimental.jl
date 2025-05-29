```
get_callbacks(c::ComponentModel)
get_callbacks(nw::Network, idx::Union{VIndex,EIndex})
```

Gets all callback functions for the component. Wraps in tuple, even if there is only a single one.
