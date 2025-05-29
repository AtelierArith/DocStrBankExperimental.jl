```
libc(p::AbstractPlatform)
```

指定された `Platform` オブジェクトのための libc を `String` として取得します。明示的な `libc` の選択肢がないプラットフォーム（ほとんどのプラットフォーム）では `nothing` を返します。

# 例

```jldoctest
julia> libc(Platform("armv7l", "Linux"))
"glibc"

julia> libc(Platform("aarch64", "linux"; libc="musl"))
"musl"

julia> libc(Platform("i686", "Windows"))
```
