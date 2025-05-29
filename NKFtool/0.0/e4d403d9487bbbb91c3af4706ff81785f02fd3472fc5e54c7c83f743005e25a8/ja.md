```
nkf_guess(from::String)
```

入力テキスト `from` のエンコーディングを推測し、そのエンコーディングを表す文字列を返します。これはコマンドライン `echo <from> | nkf -g` の結果です。

# 例

```julia-repl
julia> nkf_guess(raw"こんにちわ")
"UTF-8"

julia> nkf_convert( raw"こんにちわ", "-j") |> nkf_guess
"ISO-2022-JP"

julia> nkf_convert( raw"こんにちわ", "-e") |> nkf_guess
"EUC-JP"

julia> nkf_convert( raw"こんにちわ", "-s") |> nkf_guess
"Shift_JIS"
```
