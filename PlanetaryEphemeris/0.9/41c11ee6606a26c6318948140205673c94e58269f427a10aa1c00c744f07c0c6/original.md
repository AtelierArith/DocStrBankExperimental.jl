```
nbodyind(N::Int, i::Int)
nbodyind(N::Int, ivec::AbstractVector{Int})
```

Return the indices of the positions and velocities of the `i`-th body (or the `ivec`-th bodies) in a vector with `N` bodies. The function assumes that the vector has the form: `3N` positions + `3N` velocities (+ Lunar physical librations + TT-TDB).
