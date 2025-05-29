```
def_space_coord(nc::NCDataset, space::Spaces.AbstractSpace; type = "dgll")
```

Add spatial dimensions for `space` in the NetCDF dataset `nc`, compatible with the type used by [`remap_weights`](@ref).

If a compatible dimension already exists, it will be reused.
