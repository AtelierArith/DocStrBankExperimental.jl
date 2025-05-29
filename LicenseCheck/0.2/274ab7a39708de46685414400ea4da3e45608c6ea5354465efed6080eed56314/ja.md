```
licensecheck(text::String) -> @NamedTuple{licenses_found::Vector{String}, license_file_percent_covered::Float64}
```

`text`内で一致したライセンスの名前のベクター（より具体的には、SPDX 3.10ライセンス識別子）と、これらの一致によってカバーされるテキストのパーセントを返します。

ライセンスIDの完全なリストは[https://github.com/google/licensecheck/blob/v0.3.1/licenses/README.md](https://github.com/google/licensecheck/blob/v0.3.1/licenses/README.md)にあり、SDPX 3.10ライセンスが含まれています。[https://github.com/spdx/license-list-data/tree/v3.10/text](https://github.com/spdx/license-list-data/tree/v3.10/text)。

これは、元のGoライブラリの`licensecheck.Scan`のいくつかの機能を提供します（[https://github.com/google/licensecheck](https://github.com/google/licensecheck)）。

## 例

```julia
julia> using LicenseCheck

julia> text = read(joinpath(pkgdir(LicenseCheck), "LICENSE"), String);

julia> licensecheck(text)
(licenses_found = ["MIT"], license_file_percent_covered = 98.82352941176471)
```
