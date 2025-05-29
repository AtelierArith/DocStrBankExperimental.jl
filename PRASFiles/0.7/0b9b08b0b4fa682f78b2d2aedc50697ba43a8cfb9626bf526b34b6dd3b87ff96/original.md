```
SystemModel(filename::String)
```

Load a `SystemModel` from an appropriately-formatted HDF5 file on disk. These files typically have a .pras filename extension.

# Examples

```julia
sys = SystemModel("path/to/prasfile.pras")
```
