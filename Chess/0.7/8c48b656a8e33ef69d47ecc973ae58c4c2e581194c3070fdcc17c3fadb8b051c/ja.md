```
@game
```

`Game`を初期化するためのマクロで、手数を指定します。

キャスリングの手は、ハイフンなしで示す必要があります（つまり、「OO」または「OOO」）ので、Juliaのパーサーを満たす必要があります。

# 例

```julia-repl
julia> @game d4 Nf6 c4 e6 Nc3 Bb4 Qc2 OO
Game:
 1. d4 Nf6 2. c4 e6 3. Nc3 Bb4 4. Qc2 O-O *
```
