```
generators(L::AbstractLat; minimal = false) -> Vector{Vector}
```

Return a set of generators of the lattice `L` over the base ring of `L`.

If `minimal == true`, the number of generators is minimal. Note that computing minimal generators is expensive.
