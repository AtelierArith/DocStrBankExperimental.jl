```
find_licenses_by_list(dir) -> Vector{@NamedTuple{license_filename::String, licenses_found::Vector{String}, license_file_percent_covered::Float64}}
```

Checks to see if any license name in `LicenseCheck.LICENSE_NAMES` exists in `dir`, and if so, calls [`licensecheck`](@ref) on it. Returns the results of all existing licenses and their `licensecheck` values, sorted from highest `license_file_percent_covered` to lowest.

This function does not ever call `readdir(dir)` and instead just checks if each of the 2247 names in `LicenseCheck.LICENSE_NAMES` exists, so it can work on extremely large directories.

On case-insensitive filesystems, this can return multiple results for the same file, with different cases.
