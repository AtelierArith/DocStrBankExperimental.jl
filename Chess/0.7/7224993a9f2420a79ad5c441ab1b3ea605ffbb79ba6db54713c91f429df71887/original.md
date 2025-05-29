```
pseudoislegal(b::Board, m::Move)::Bool
```

Tests whether the pseudo-legal move `m` is legal.

# Examples

```julia-repl
julia> b = @startboard e4 c5 Nf3 d6 Bb5;

julia> pseudoislegal(b, Move(SQ_C8, SQ_D7))
true

julia> pseudoislegal(b, Move(SQ_G8, SQ_F6))
false
```
