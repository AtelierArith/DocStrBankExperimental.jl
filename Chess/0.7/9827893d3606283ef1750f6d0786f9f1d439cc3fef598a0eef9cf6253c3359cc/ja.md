```
domove(b::Board, m::Move)
domove(b::Board, m::String)
```

ボード `b` 上で移動 `m` を行い、新しいボードを返します。

ボード `b` 自体は変更されず、新しいボードが返されます。高いパフォーマンスが要求される場合は、代わりに破壊的な関数 `domove!()` を呼び出すべきです。

提供された移動が文字列の場合、この関数はまずその移動を UCI 移動として解析しようとし、次に SAN 移動として解析します。

`m` がこのボード上で合法的な移動であることを確認するのは呼び出し元の責任です。

# 例

```julia-repl
julia> b = startboard();

julia> domove(b, "Nf3")
Board (rnbqkbnr/pppppppp/8/8/8/5N2/PPPPPPPP/RNBQKB1R b KQkq -):
 r  n  b  q  k  b  n  r
 p  p  p  p  p  p  p  p
 -  -  -  -  -  -  -  -
 -  -  -  -  -  -  -  -
 -  -  -  -  -  -  -  -
 -  -  -  -  -  N  -  -
 P  P  P  P  P  P  P  P
 R  N  B  Q  K  B  -  R
```
