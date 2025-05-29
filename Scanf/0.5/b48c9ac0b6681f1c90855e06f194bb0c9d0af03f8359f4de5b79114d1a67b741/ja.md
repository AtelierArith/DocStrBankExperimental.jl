```
@scanf([io:Union{IO,String}, ], "%Fmt", args::...)
```

C `scanf` スタイルのフォーマット指定文字列を使用して入力ストリームまたは文字列をスキャンし、引数に値を割り当てます。

フォーマット文字列（変数ではない）は、マクロ展開時に解析されます。`scanf(io, Scanf.format"%Fmt", args...)` と同等です。

# 例

```jldoctest
r, a... = @scanf("%f%f%f%f", zeros(4)...)

julia> r, a, b = @scanf "23.4 text" "%f %2s" Float64 String
(2, 23.4, "te")
```
