```
struct OpaqueContent
```

特定のMIMEタイプを持つ不透明なコンテンツを表します。

コンストラクタ:

```julia
OpaqueContent(data::AbstractVector{UInt8}, mime::MIME)

OpaqueContent(mime::MIME) do io
    # io::IOに何かを追加します
end
```

例:

content = OpaqueContent(MIME("text/html")) do io     println(io, "<p>Hello, World!</p>") end lazyreport(content)
