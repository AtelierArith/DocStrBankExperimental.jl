```
CompressionSettings(enabled, type, level, shuffle)
```

Provides customization of HDF5 compression settings.

  * `enabled::Bool`: Controls whether compression is enabled.
  * `type::InfrastructureSystems.CompressionTypesModule.CompressionTypes`: Specifies the type of compression to use.
  * `level::Int64`: Supported values are 0-9. Higher values deliver better compression ratios but take longer.
  * `shuffle::Bool`: Controls whether to enable the shuffle filter. Used with DEFLATE.

Refer to the [HDF5.jl](https://juliaio.github.io/HDF5.jl/stable/) and [HDF5](https://portal.hdfgroup.org/) documentation for more details on the options.

# Example

```julia
settings = CompressionSettings(
    enabled = true,
    type = CompressionTypes.DEFLATE,  # BLOSC is also supported
    level = 3,
    shuffle = true,
)
```
