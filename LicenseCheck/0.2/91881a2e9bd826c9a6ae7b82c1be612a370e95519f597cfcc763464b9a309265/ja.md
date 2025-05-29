```
find_license(dir; max_bytes = MAX_LICENSE_SIZE_IN_BYTES) -> Union{Nothing, @NamedTuple{license_filename::String, licenses_found::Vector{String}, license_file_percent_covered::Float64}}
```

`license_file_percent_covered`が最も高いライセンスを[`find_licenses`](@ref)から返します。ライセンスコンテンツが見つかったファイルがある場合は、`nothing`を返します。

## 例

```julia
julia> find_license(".")
(license_filename = "LICENSE", licenses_found = ["MIT"], license_file_percent_covered = 98.82352941176471)

```
