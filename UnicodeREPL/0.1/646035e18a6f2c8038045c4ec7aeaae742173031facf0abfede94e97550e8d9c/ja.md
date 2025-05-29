```
ufind(r::Union{AbstractString,Regex})
```

`r` に一致するキーを持つ Unicode 補完ペアを返します

## 例

```julia-repl
julia> using UnicodeREPL
REPL モード unicode_repl が初期化されました。^ を押して入力し、バックスペースで終了します。

julia> ufind("feed")
2-element Vector{Pair{String, String}}:
 "\\:breast-feeding:" => "🤱"
         "\\linefeed" => "↴"

julia> ufind(r"^[^:]*feed")
1-element Vector{Pair{String, String}}:
 "\\linefeed" => "↴"

julia>
```

Unicode コードページ自体は含まれていないため、マッピング `"\\u(feed)" => "ﻭ"` は出力に含まれません。
