```
find_licenses(dir; allow_brute=true, max_bytes = MAX_LICENSE_SIZE_IN_BYTES) -> Vector{@NamedTuple{license_filename::String, licenses_found::Vector{String}, license_file_percent_covered::Float64}}
```

ディレクトリ `dir` のトップレベルにある可能性のあるライセンスのテーブルを、そのパスと [`licensecheck`](@ref) の結果と共にコンパイルし、`license_file_percent_covered` でソートします。サイズが100未満のディレクトリには [`find_licenses_by_bruteforce`](@ref) を使用し、より大きなディレクトリには [`find_licenses_by_list_intersection`](@ref) を使用します。

`allow_brute=false` の場合は、単に [`find_licenses_by_list_intersection`](@ref) のエイリアスとして機能します。

## 例

```julia
julia> find_licenses(".")
1-element Vector{NamedTuple{(:license_filename, :licenses_found, :license_file_percent_covered), Tuple{String, Vector{String}, Float64}}}:
 (license_filename = "LICENSE", licenses_found = ["MIT"], license_file_percent_covered = 98.82352941176471)

```
