```
queryparampairs(::URI) -> Vector{Pair{String, String}}
queryparampairs(query_str::AbstractString) -> Vector{Pair{String, String}}
```

`queryparams`と同様ですが、`key=value`ペア形式の規約に従って解析された`query`パラメータ文字列を含む`Vector{Pair{String, String}}`を返します。

これは正式なURI文法の一部ではなく、一般的な解析規約です — [RFC 3986](https://tools.ietf.org/html/rfc3986#section-3.4)を参照してください。
