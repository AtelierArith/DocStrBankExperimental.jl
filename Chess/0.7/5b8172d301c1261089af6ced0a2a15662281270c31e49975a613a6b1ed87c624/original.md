```
from(m::Move)
```

The source square of a move.

# Examples

```julia-repl
julia> Move(SQ_D2, SQ_D4)
Move(d2d4)

julia> from(Move(SQ_G1, SQ_F3))
SQ_G1

julia> from(Move(SQ_C7, SQ_C8, QUEEN))
SQ_C7
```
