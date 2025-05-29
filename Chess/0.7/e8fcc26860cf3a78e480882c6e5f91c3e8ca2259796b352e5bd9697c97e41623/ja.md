```
piecefromchar(ch::Char)
```

文字を `Piece` に変換しようとします。

返り値は `Union{Piece, Nothing}` です。入力された文字が有効な英語の駒の文字であれば、対応する駒が返されます。駒の文字が大文字であれば、その駒は白です。駒の文字が小文字であれば、その駒は黒です。

入力値が有効な英語の駒の文字でない場合、関数は `nothing` を返します。

# 例

```julia-repl
julia> piecefromchar('Q')
PIECE_WQ

julia> piecefromchar('n')
PIECE_BN

julia> piecefromchar('-') == nothing
true
```
