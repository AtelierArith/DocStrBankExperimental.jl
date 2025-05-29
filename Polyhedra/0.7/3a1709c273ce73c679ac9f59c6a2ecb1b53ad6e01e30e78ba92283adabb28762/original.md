```
project(p::Polyhedron, pset, algo)
```

Equivalent to `eliminate(p, setdiff(1:fulldim(p), pset), algo)`.
