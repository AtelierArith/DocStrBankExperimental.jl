```
macos_version(p::AbstractPlatform)
```

`p`に`os_version`が指定されていない場合、私たちがJuliaの世界でサポートしている最も古いバージョンである`macOS 10.8`（カーネルバージョン14）をデフォルトとしますが、実際に指定されている場合は、指定された値（カーネルバージョンからmacOSバージョンへのマッピング）を返します。

```jldoctest
julia> macos_version(Platform("x86_64", "macos"; os_version="18"))
"10.14"
```
