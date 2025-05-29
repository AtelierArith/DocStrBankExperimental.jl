```
VTUFile(name::String)
```

Loads a VTU file. Don't forget to set the proper fieldnames via `set_uncompress_keywords` and `set_interpolation_keywords`.

# Constructor

  * `name::String`: path to vtu file

# Fields

  * `name::String`: path to vtu file; destination for file writing
  * `xmlroot::AbstractXMLElement`: VTU file in XML represantation
  * `dataarrays::Vector{AbstractXMLElement}`: Vector with all XML elements with tag `DataArray` of VTU file
  * `headertype::Union{Type{UInt32},Type{UInt64}}`: type of header
  * `offsets::Vector{Int}`: Offset of each field data in the compressed appended data
  * `data::VTUData`: Conatainer with  [`VTUData`](@ref)
  * `compressed_dat::Bool` : True if data is compressed

# Example

```julia
set_uncompress_keywords("temperature","points")
set_interpolation_keywords("temperature")
vtufile = VTUFile("./path-to-vtu/example.vtu");
```
