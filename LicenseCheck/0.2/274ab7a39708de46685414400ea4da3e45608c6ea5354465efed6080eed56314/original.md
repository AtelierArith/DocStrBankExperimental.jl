```
licensecheck(text::String) -> @NamedTuple{licenses_found::Vector{String}, license_file_percent_covered::Float64}
```

Returns a vector of the names of licenses (more specifically, the SPDX 3.10 license identifiers) matched in `text` and the percent of the text covered by these matches.

The full list of license IDs is located at [https://github.com/google/licensecheck/blob/v0.3.1/licenses/README.md](https://github.com/google/licensecheck/blob/v0.3.1/licenses/README.md), and includes the SDPX 3.10 licenses, [https://github.com/spdx/license-list-data/tree/v3.10/text](https://github.com/spdx/license-list-data/tree/v3.10/text).

This provides some of the functionality of `licensecheck.Scan` in the original Go library ([https://github.com/google/licensecheck](https://github.com/google/licensecheck)).

## Example

```julia
julia> using LicenseCheck

julia> text = read(joinpath(pkgdir(LicenseCheck), "LICENSE"), String);

julia> licensecheck(text)
(licenses_found = ["MIT"], license_file_percent_covered = 98.82352941176471)
```
