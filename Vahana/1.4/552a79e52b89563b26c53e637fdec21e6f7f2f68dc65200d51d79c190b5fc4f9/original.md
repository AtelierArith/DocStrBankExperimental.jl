```
create_enum_converter()
```

The HDF5.jl library does not support Enums as fields of structs that should be stored. This function add this support but as this involves type piracy, this support must be enabled explicitly.
