```
ZipArchive(data::Vector{UInt8}; flags::Int = LIBZIP_RDONLY) -> ZipArchive
ZipArchive(; flags::Int = LIBZIP_CREATE) -> ZipArchive
```

Construct an empty [`ZipArchive`](@ref) or an existing one from an in-memory byte buffer with specified `flags`.

See also [`Open flags`](@ref open_flags) section.

## Examples

```julia-repl
julia> ZipArchive(; flags = LIBZIP_CREATE | LIBZIP_CHECKCONS)
 ZipArchive:
    🔓 Archive is open and ready for use!
    📂 The archive is empty.
```

```julia-repl
julia> zip_file = read(".../secrets.zip");

julia> ZipArchive(zip_file)
 ZipArchive:
    🔓 Archive is open and ready for use!
    📁 Files in archive:
      📄 my_secret_1.txt/: 42 bytes
      [...]
```
