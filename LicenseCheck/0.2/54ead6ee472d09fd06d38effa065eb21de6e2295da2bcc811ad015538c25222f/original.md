```
find_licenses_by_list_intersection(dir) -> Vector{@NamedTuple{license_filename::String, licenses_found::Vector{String}, license_file_percent_covered::Float64}}
```

Checks to see if any license name in `LicenseCheck.LICENSE_NAMES` exists in `dir`, and if so, calls [`licensecheck`](@ref) on it. Returns the results of all existing licenses and their `licensecheck` values, sorted from highest `license_file_percent_covered` to lowest.

Operates by filtering the results of `readdir`, which should be efficient for small and moderately sized directories. See [`find_licenses_by_list`](@ref) for an alternate approach for very large directories.
