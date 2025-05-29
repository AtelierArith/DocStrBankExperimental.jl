```
nkf_convert(from::IO, options="-w -m0")
```

入力ストリーム `from` をオプション指令 `options` で指定されたエンコーディングに変換し、出力テキスト文字列を返します。これは、コマンドライン `cat <from> | nkf <options>` の結果です。

# 引数

  * `text::String`: 入力文字列
  * `options::String`: nkf コマンドに渡される指令。 [`nkf_convert(from::String, options="-w -m0")`](@ref) を参照してください。

# 例

```julia-repl
julia> open("hello_sjis.txt","w") do f
           print(f, nkf_convert(raw"こんにちわ", "-s"))
       end
       #
       hello_utf=open("hello_sjis.txt") do f
           nkf_convert(f, "-w -m0")
       end
"こんにちわ"
```
