```
find_license(dir; max_bytes = MAX_LICENSE_SIZE_IN_BYTES) -> Union{Nothing, @NamedTuple{license_filename::String, licenses_found::Vector{String}, license_file_percent_covered::Float64}}
```

Returns the license with the highest `license_file_percent_covered` from [`find_licenses`](@ref). If file is found with any license content, returns `nothing`.

## Example

```julia
julia> find_license(".")
(license_filename = "LICENSE", licenses_found = ["MIT"], license_file_percent_covered = 98.82352941176471)

```
