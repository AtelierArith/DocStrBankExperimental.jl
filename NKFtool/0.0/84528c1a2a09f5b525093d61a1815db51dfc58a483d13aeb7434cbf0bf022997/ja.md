```
nkf_convert(from::String, options="-w -m0")
```

入力文字列 `from` をオプション指令 `options` で指定されたエンコーディングに変換し、コマンドライン `echo <from> | nkf <options>` の結果である出力テキスト文字列を返します。

# 引数

  * `from::String`: 入力文字列
  * `options::String`: nkf コマンドに渡されるオプション指令。

      * 出力エンコーディング

          * `-j` : ISO-2022-JP
          * `-s` : Shift_JIS
          * `-e` : EUC-JP
          * `-w[8[0],{16,32}[{B,L}[0]]]` : オプション付き UTF
      * 入力エンコーディング

          * `-J` : ISO-2022-JP
          * `-S` : Shift_JIS
          * `-E` : EUC-JP
          * `-W[8,[16,32][B,L]]` : オプション付き UTF
      * MIME デコード : `-m[BQSN0]`

          * B:base64
          * Q:quoted
          * S:strict
          * N:nonstrict
          * 0:デコードしない
      * MIME エンコード : `-M[BQ]`

          * B:base64
          * Q:quoted

# 例

```julia-repl
julia> nkf_convert(raw"こんにちわ", "-w -m0")
"こんにちわ"

julia> using Base64

julia> nkf_convert( raw"こんにちわ", "-j") |> base64encode
"GyRCJDMkcyRLJEEkbxsoQg=="

julia> String(base64decode(ans)) |> nkf_convert
"こんにちわ"
```
