```
find_licenses_by_list_intersection(dir) -> Vector{@NamedTuple{license_filename::String, licenses_found::Vector{String}, license_file_percent_covered::Float64}}
```

`LicenseCheck.LICENSE_NAMES` にあるライセンス名が `dir` に存在するかどうかを確認し、存在する場合は [`licensecheck`](@ref) を呼び出します。すべての既存のライセンスとその `licensecheck` 値の結果を、`license_file_percent_covered` が高い順から低い順にソートして返します。

`readdir` の結果をフィルタリングすることで動作し、小規模および中規模のディレクトリに対して効率的であるべきです。非常に大きなディレクトリに対する代替アプローチについては、[`find_licenses_by_list`](@ref) を参照してください。
