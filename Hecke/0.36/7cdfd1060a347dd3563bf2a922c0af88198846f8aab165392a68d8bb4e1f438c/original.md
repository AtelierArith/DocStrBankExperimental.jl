```
is_modular(L::AbstractLat, p) -> Bool, Int
```

Return whether the completion $L_{p}$ of the lattice `L` at the prime ideal or integer `p` is modular. If it is the case the second returned value is an integer `v` such that $L_{p}$ is $p^v$-modular.
