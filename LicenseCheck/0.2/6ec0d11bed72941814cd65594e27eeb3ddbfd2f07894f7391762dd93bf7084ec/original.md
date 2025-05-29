```
find_licenses(dir; allow_brute=true, max_bytes = MAX_LICENSE_SIZE_IN_BYTES) -> Vector{@NamedTuple{license_filename::String, licenses_found::Vector{String}, license_file_percent_covered::Float64}}
```

Compiles a table of possible licenses at the top-level of a directory `dir` with their path and the results of [`licensecheck`](@ref), sorted by `license_file_percent_covered`. Uses [`find_licenses_by_bruteforce`](@ref) for directories with size less than 100 and [`find_licenses_by_list_intersection`](@ref) for larger directories.

Simply acts as an alias for [`find_licenses_by_list_intersection`](@ref) if `allow_brute=false`.

## Example

```julia
julia> find_licenses(".")
1-element Vector{NamedTuple{(:license_filename, :licenses_found, :license_file_percent_covered), Tuple{String, Vector{String}, Float64}}}:
 (license_filename = "LICENSE", licenses_found = ["MIT"], license_file_percent_covered = 98.82352941176471)

```
