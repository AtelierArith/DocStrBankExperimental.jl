```
nkf_guess(from::IO)
```

入力ストリーム `from` のエンコーディングを推測し、そのエンコーディングを表す文字列を返します。

# 例

```julia-repl
julia> nkf_guess(IOBuffer(raw"こんにちわ"))
"UTF-8"

julia> open("hello_sjis.txt","w") do f
           print(f, nkf_convert(raw"こんにちわ", "-s"))
       end
       #
       encoding=open("hello_sjis.txt") do f
           nkf_guess(f)
       end
"Shift_JIS"
```
