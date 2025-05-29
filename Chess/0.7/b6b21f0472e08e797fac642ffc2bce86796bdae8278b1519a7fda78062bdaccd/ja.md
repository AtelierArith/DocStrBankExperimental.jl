```
filefromchar(c::Char)
```

文字をファイルに変換しようとします。

返り値は `Union{SquareFile, Nothing}` です。文字が有効なファイルを表さない場合は `nothing` が返されます。

# 例

```julia-repl
julia> filefromchar('c')
FILE_C

julia> filefromchar('2') == nothing
true
```
