```
piecetypefromchar(c::Chars)
```

文字を `PieceType` に変換しようとします。

返り値は `Union{PieceType, Nothing}` です。入力された文字が有効な大文字または小文字の英語の駒の文字（PNBRQK）であれば、関数は対応する駒のタイプを返します。それ以外の入力文字に対しては、関数は `nothing` を返します。

# 例

```julia-repl
julia> piecetypefromchar('n') == KNIGHT
true

julia> piecetypefromchar('B') == BISHOP
true

julia> piecetypefromchar('a') == nothing
true
```
