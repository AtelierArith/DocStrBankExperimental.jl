```julia
max_rev(a, b, c)

```

Reverse McCormick operator for `max(::MC, ::MC)`. Note that this function is not invertible. If `b` dominates `c`, the  `b = b ∩ a`. If `c` dominates `b`,  `c = c ∩ a`. No update otherwise. TODO: See if constructing an reverse from the identity `max(x,y) = 0.5*(x + y + abs(x - y))` yields a tigher relaxation in this case.
