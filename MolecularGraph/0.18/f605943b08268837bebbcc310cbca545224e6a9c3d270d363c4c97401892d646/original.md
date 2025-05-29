```
remove_hydrogens!(mol::SimpleMolGraph{T,V,E}) -> Vector{T}
```

Remove following hydrogen vertices from the molecule: that are not charged, have no unpaired electron, have no specific mass, are non-stereospecific and are attached to organic heavy atoms.

This returns vmap array similar to `Graphs.rem_vertices!`.
