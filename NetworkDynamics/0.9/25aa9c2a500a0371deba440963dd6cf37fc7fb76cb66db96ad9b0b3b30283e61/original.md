```
add_callback!(c::ComponentModel, cb; check=true)
add_callback!(nw::Network, idx::Union{VIndex,EIndex}, cb; check=true)
```

Adds a callback function to the component. Does not overwrite existing callbacks. See also [`set_callback!`](@ref).
