```
arch(p::AbstractPlatform)
```

与えられた `Platform` オブジェクトのアーキテクチャを `String` として取得します。

# 例

```jldoctest
julia> arch(Platform("aarch64", "Linux"))
"aarch64"

julia> arch(Platform("amd64", "freebsd"))
"x86_64"
```
