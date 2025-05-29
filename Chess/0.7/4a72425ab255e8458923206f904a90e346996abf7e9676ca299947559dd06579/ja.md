```
@addmoves!(game, moves...)
```

ゲーム `game` に一連の手を追加するためのマクロです。

キャスリングの手は、ハイフンなしで示す必要があります（つまり、「OO」または「OOO」）ので、Julia のパーサーを満たす必要があります。

# 例

```julia-repl
julia> g = @game e4 c5
Game:
 1. e4 c5 *

julia> @addmoves! g Nf3 Nc6
Game:
 1. e4 c5 2. Nf3 Nc6 *

julia> g = @game e4 e5 Nf3; back!(g); back!(g)
Game:
 1. e4 * e5 2. Nf3

julia> @addmoves! g c5 b4 cxb4
Game:
 1. e4 e5 (1... c5 2. b4 cxb4 *) 2. Nf3
```
