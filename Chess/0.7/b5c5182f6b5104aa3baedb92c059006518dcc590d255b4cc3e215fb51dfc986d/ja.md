```
domove!(b::Board, m::Move)
domove!(b::Board, m::String)
```

ボード `b` を破壊的に変更し、移動 `m` を行います。

提供された移動が文字列の場合、この関数は最初に移動をUCI移動として解析し、次にSAN移動として解析しようとします。

移動 `m` が合法であることを確認するのは呼び出し元の責任です。

この関数は `UndoInfo` 型の値を返します。これは、後で `undomove!()` を呼び出して移動を取り消し、元の位置に戻す場合に必要です。

# 例

```julia-repl
julia> b = startboard();

julia> domove!(b, "d4");

julia> b
Board (rnbqkbnr/pppppppp/8/8/3P4/8/PPP1PPPP/RNBQKBNR b KQkq -):
 r  n  b  q  k  b  n  r
 p  p  p  p  p  p  p  p
 -  -  -  -  -  -  -  -
 -  -  -  -  -  -  -  -
 -  -  -  P  -  -  -  -
 -  -  -  -  -  -  -  -
 P  P  P  -  P  P  P  P
 R  N  B  Q  K  B  N  R
```
