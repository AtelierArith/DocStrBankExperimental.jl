```
os(p::AbstractPlatform)
```

指定された `Platform` オブジェクトのオペレーティングシステムを `String` として取得します。

# 例

```jldoctest
julia> os(Platform("armv7l", "Linux"))
"linux"

julia> os(Platform("aarch64", "macos"))
"macos"
```
