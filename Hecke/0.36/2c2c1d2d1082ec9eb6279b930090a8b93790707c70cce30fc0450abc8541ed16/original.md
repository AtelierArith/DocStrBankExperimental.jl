```
is_modular(L::AbstractLat) -> Bool, AbsSimpleNumFieldOrderFractionalIdeal
```

Return whether the lattice `L` is modular. In this case, the second returned value is a fractional ideal $\mathfrak a$ of the base algebra of `L` such that $\mathfrak a L^\# = L$, where $L^\#$ is the dual of `L`.
