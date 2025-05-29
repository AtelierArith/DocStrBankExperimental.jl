```
molecules(::System{T} = default_system())
```

Returns a `MoleculeTable{T}` containing all molecules of the given system.

# Supported keyword arguments

  * `variant::Union{Nothing, MoleculeVariantType} = nothing`

The keyword argument limits the results to molecules matching the given variant type. Keyword arguments set to `nothing` are ignored.
