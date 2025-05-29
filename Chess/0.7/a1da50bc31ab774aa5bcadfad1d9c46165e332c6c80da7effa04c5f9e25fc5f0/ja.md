```
@domoves!(game, moves...)
```

`game`に手を追加し、既存の継続を削除するためのマクロです。

キャスリングの手は、ハイフンなしで示す必要があります（つまり、「OO」または「OOO」）ので、Juliaのパーサーを満たすことができます。

このマクロは、ゲームの現在のポイントから既存の継続をすべて削除します。これが望ましくない場合は、代わりに`@addmoves!`マクロを使用してください。

# 例

```julia-repl
julia> g = @game e4 e5 Nf3; back!(g); back!(g)
Game:
 1. e4 * e5 2. Nf3

julia> @domoves! g c5 b4 cxb4
Game:
 1. e4 c5 2. b4 cxb4 *
```
