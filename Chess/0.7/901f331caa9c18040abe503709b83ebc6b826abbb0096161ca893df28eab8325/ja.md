```
moveischeck(b::Board, m::Move)
```

移動 `m` がチェックの移動であるかどうかを判断します。

キャスリングチェックの（珍しい）ケースにはまだ対応していません。

# 例

```julia-repl
julia> b = @startboard e4 c5 Nf3 d6;

julia> moveischeck(b, Move(SQ_F1, SQ_B5))
true

julia> moveischeck(b, Move(SQ_D2, SQ_D4))
false
```
