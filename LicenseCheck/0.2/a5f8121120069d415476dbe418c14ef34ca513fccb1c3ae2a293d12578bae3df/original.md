```
find_licenses_by_bruteforce(dir; max_bytes = LicenseCheck.MAX_LICENSE_SIZE_IN_BYTES) -> Vector{@NamedTuple{license_filename::String, licenses_found::Vector{String}, license_file_percent_covered::Float64}}
```

Calls [`licensecheck`](@ref) on every plaintext file in `dir` whose size is less than `max_bytes`, returning the results as a table. The parameter `max_bytes` defaults to 459 KiB.
