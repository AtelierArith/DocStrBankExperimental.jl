```
pseudoislegal(b::Board, m::Move)::Bool
```

擬似合法な手 `m` が合法かどうかをテストします。

# 例

```julia-repl
julia> b = @startboard e4 c5 Nf3 d6 Bb5;

julia> pseudoislegal(b, Move(SQ_C8, SQ_D7))
true

julia> pseudoislegal(b, Move(SQ_G8, SQ_F6))
false
```
