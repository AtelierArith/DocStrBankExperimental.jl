```
set_callback!(c::ComponentModel, cb; check=true)
set_callback!(nw::Network, idx::Union{VIndex,EIndex}, cb; check=true)
```

Sets the callback function for the component. Overwrites any existing callback. See also [`add_callback!`](@ref).
