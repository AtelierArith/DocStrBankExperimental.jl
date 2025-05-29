```
moveispseudo(b::Board, m::Move)
```

Test whether the move `m` is pseudo-legal.

This means that the move `m` is legal except for possibly leaving the king in check.

# Examples

```julia-repl
julia> b = @startboard e4 c5 Nf3 d6 Bb5;

julia> moveispseudo(b, Move(SQ_G8, SQ_F6))
true

julia> moveispseudo(b, Move(SQ_B8, SQ_C6))
true

julia> moveispseudo(b, Move(SQ_G8, SQ_G6))
false
```
