```
removable_hydrogens(mol::SimpleMolGraph{T,V,E}) -> Vector{T}
```

Return a vector of removable hydrogen nodes.

Removable hydrogens are not charged, have no unpaired electron, have no specific mass, are non-stereospecific and are attached to organic heavy atoms.
