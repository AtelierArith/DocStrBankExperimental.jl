```
mimes_from_fileext(fileext::Union{Symbol,AbstractString}) -> mimes::Vector{Symbol}
```

List MIMEs `mimes` known to be used for file extention `fileext`.  Return an empty tuple if not found.

# Example

```jldoctest
julia> using MIMEFileExtensions

julia> mimes_from_fileext("txt")
1-element Vector{Symbol}:
 Symbol("text/plain")
```
