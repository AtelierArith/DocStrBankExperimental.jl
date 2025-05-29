```
@simplegame
```

`SimpleGame`を初期化するためのマクロで、いくつかの手を指定します。

キャスリングの手は、ハイフンなしで示す必要があります（つまり、「OO」または「OOO」）ので、Juliaのパーサーを満たすことができます。

# 例

```julia-repl
julia> @simplegame d4 Nf6 c4 e6 Nc3 Bb4 Qc2 OO
SimpleGame:
 1. d4 Nf6 2. c4 e6 3. Nc3 Bb4 4. Qc2 O-O *
```
