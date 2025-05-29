```
queryparams(::URI) -> Dict
queryparams(query_str::AbstractString) -> Dict
```

`query` パラメータ文字列をキー=値ペアのフォーマット規約に従って解析した `Dict` を返します。

重複するクエリパラメータの値はサポートされていないことに注意してください。必要な場合は `queryparampairs` を使用してください。

これは正式なURI文法の一部ではなく、一般的な解析規約に過ぎないことに注意してください — [RFC 3986](https://tools.ietf.org/html/rfc3986#section-3.4) を参照してください。
