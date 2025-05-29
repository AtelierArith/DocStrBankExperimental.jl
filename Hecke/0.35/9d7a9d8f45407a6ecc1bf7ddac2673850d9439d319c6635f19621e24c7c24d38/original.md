```
in(L::HermLat, g::HermLocalGenus) -> Bool
```

Return whether `g` and the local genus symbol of the completion of the hermitian lattice `L` at `prime(g)` agree. Note that `L` being in `g` requires both `L` and `g` to be defined over the same extension $E/K$.
