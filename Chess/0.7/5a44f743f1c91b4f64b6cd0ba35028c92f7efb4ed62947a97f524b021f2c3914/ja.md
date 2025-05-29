```
moveispseudo(b::Board, m::Move)
```

移動 `m` が擬似合法であるかどうかをテストします。

これは、移動 `m` が合法であるが、王をチェックに置く可能性があることを意味します。

# 例

```julia-repl
julia> b = @startboard e4 c5 Nf3 d6 Bb5;

julia> moveispseudo(b, Move(SQ_G8, SQ_F6))
true

julia> moveispseudo(b, Move(SQ_B8, SQ_C6))
true

julia> moveispseudo(b, Move(SQ_G8, SQ_G6))
false
```
