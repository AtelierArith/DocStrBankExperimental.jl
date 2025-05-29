```
make_supercell(g::PeriodicGraph, t)
```

Return a graph isomorphic to the input `g` whose its unit cell is a repetition of that of `g`, each dimension `i` being repeated `t[i]` times. It follows that the number of vertices of `make_supercell(g, t)` is `prod(t)*nv(g)`

`t` must be an interator over positive integers.
