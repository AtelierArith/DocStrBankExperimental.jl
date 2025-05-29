```
ZipFile
```

Represents a file contained in an [`ZipArchive`](@ref).

## Fields

  * `body::Vector{UInt8}`: Binary representation of file contents.
  * `name::String`: File name.
  * `index::Int64`: File index number (zero-based).
  * `size::Int64`: File uncompressed size.
  * `comp_size::Int64`: File compressed size.
  * `time::DateTime`: File last modification time.
  * `crc::Int64`: File CRC-32 checksum.
  * `comp_method::Int64`: File compression method.
  * `encryption_method::Int64`: File encryption method.
