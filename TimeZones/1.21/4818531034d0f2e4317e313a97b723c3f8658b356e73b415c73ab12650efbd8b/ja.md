```
TimeZone(str::AbstractString) -> TimeZone
```

文字列に基づいて `TimeZone` サブタイプを構築します。文字列が認識された標準のタイムゾーン名である場合、データはコンパイルされた IANA タイムゾーンデータベースからロードされます。それ以外の場合、文字列は固定タイムゾーンとして解析されます。

認識された標準およびレガシータイムゾーン名のリストは、`timezone_names()` を実行することで入手できます。サポートされている固定タイムゾーン文字列形式は、[`FixedTimeZone(::AbstractString)`](@ref) のドキュメントに記載されています。

## 例

```jldoctest
julia> TimeZone("Europe/Warsaw")
Europe/Warsaw (UTC+1/UTC+2)

julia> TimeZone("UTC")
UTC
```
