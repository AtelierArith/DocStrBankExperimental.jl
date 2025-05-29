```
domoves!(b::Board, moves::Vararg{Move})
domoves!(b::Board, moves::Vararg{String}; movelist::MoveList = MoveList(200))
```

ボード b を破壊的に変更し、一連の手を実行します。

提供された手が文字列の場合、この関数はまず手を UCI 手として解析し、UCI 手の解析が失敗した場合は SAN 手として解析しようとします。

すべての手が合法であることを確認するのは呼び出し元の責任です。通常の手が違法である場合、その結果は未定義です。手の文字列が明確な合法的な手として解析できない場合、関数は例外をスローします。

`move::Vararg{String}` の場合、`movefromsan` が呼び出されます。不要な割り当てによる時間/スペースの節約のために、事前に割り当てられた `MoveList` を提供することができます。提供された場合、`movelist` パラメータは `movefromsan` に渡されます。`movelist` が十分な容量を持っていることを確認するのは呼び出し元の責任です。

このバージョンの非破壊的なバージョンもあり、`domoves` という名前です。

# 例

```julia-repl
julia> b = startboard();

julia> domoves!(b, "e4", "c5", "Nf3", "d6", "d4", "cxd4", "Nxd4", "Nf6", "Nc3");

julia> b
Board (rnbqkb1r/pp2pppp/3p1n2/8/3NP3/2N5/PPP2PPP/R1BQKB1R b KQkq -):
 r  n  b  q  k  b  -  r
 p  p  -  -  p  p  p  p
 -  -  -  p  -  n  -  -
 -  -  -  -  -  -  -  -
 -  -  -  N  P  -  -  -
 -  -  N  -  -  -  -  -
 P  P  P  -  -  P  P  P
 R  -  B  Q  K  B  -  R

julia> b = startboard();

julia> domoves!(b, "e4", "Qxe4+")
ERROR: "Illegal or ambiguous move: Qxe4+"
```
