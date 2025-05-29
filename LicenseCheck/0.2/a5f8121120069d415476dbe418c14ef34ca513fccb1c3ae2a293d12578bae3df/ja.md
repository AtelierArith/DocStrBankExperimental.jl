```
find_licenses_by_bruteforce(dir; max_bytes = LicenseCheck.MAX_LICENSE_SIZE_IN_BYTES) -> Vector{@NamedTuple{license_filename::String, licenses_found::Vector{String}, license_file_percent_covered::Float64}}
```

ディレクトリ `dir` 内のすべてのプレーンテキストファイルに対して、サイズが `max_bytes` 未満のファイルに対して [`licensecheck`](@ref) を呼び出し、結果をテーブルとして返します。パラメータ `max_bytes` のデフォルトは 459 KiB です。
