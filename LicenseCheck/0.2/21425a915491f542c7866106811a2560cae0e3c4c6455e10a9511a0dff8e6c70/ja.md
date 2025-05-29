```
find_licenses_by_list(dir) -> Vector{@NamedTuple{license_filename::String, licenses_found::Vector{String}, license_file_percent_covered::Float64}}
```

`LicenseCheck.LICENSE_NAMES` にあるライセンス名が `dir` に存在するかどうかを確認し、存在する場合は [`licensecheck`](@ref) を呼び出します。すべての既存のライセンスとその `licensecheck` 値の結果を、`license_file_percent_covered` が高い順から低い順にソートして返します。

この関数は `readdir(dir)` を呼び出すことはなく、代わりに `LicenseCheck.LICENSE_NAMES` にある2247の名前がそれぞれ存在するかどうかを確認するため、非常に大きなディレクトリでも動作します。

大文字と小文字を区別しないファイルシステムでは、同じファイルに対して異なるケースで複数の結果が返されることがあります。
