```
remove_all_hydrogens!(mol::SimpleMolGraph{T,V,E}) -> Vector{T}
```

Remove all hydrogen vertices from the molecule.

This returns vmap array similar to `Graphs.rem_vertices!`.
