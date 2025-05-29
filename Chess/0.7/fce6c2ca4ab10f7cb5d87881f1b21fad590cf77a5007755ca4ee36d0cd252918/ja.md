```
colorfromchar(c::Char)
```

文字を `PieceColor` に変換しようとします。

返り値は `Union{PieceColor, Nothing}` です。入力文字が4つの文字 `'w'`、`'b'`、`'W'`、`'B'` のいずれかであれば、関数は明らかな対応する色（`WHITE` または `BLACK`）を返します。それ以外の入力文字の場合、関数は `nothing` を返します。

# 例

```julia-repl
julia> colorfromchar('w') == WHITE
true

julia> colorfromchar('B') == BLACK
true

julia> colorfromchar('x') == nothing
true
```
