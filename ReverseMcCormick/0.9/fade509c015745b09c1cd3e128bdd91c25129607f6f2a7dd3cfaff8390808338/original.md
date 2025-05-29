```julia
min_rev(a, b, c)

```

Reverse McCormick operator for `min`. Note that this function is not invertible. If `b` dominates `c`, the  `b = b ∩ a`. If `c` dominates `b`,  `c = c ∩ a`. No update otherwise.  TODO: See if constructing an reverse from the identity `min(x, y) = 0.5*(x + y - abs(x - y))` yields a tigher relaxation in this case.
