```
isok(p::Piece)
```

`Piece` 値が有効かどうかをテストします。

ピースの色とタイプがそれぞれ有効なピースの色とピースのタイプの値である場合に限り、`true` を返します。

# 例

```julia-repl
julia> isok(PIECE_WB)
true

julia> isok(PIECE_BQ)
true

julia> isok(EMPTY)
false

julia> isok(Piece(-10))
false
```
