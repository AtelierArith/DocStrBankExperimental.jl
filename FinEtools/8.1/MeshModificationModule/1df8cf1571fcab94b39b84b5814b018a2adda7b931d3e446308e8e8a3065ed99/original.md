```
meshsmoothing(fens::FENodeSet, fes::T; options...) where {T<:AbstractFESet}
```

General smoothing of meshes.

# Keyword options

`method` = :taubin (default) or :laplace `fixedv` = Boolean array, one entry per vertex: is the vertex immovable (true)     or movable  (false) `npass` = number of passes (default 2)

# Return

The modified  node set.
