```
wordsize(p::AbstractPlatform)
```

指定された `Platform` オブジェクトのワードサイズを取得します。

# 例

```jldoctest
julia> wordsize(Platform("armv7l", "linux"))
32

julia> wordsize(Platform("x86_64", "macos"))
64
```
