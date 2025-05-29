```
load_bz(::IBZ, A, B, species::AbstractVector, positions::AbstractMatrix; kws...)
```

`species` must have distinct labels for each atom type (e.g. can be any string or integer) and `positions` must be a matrix whose columns give the coordinates of the atom of the corresponding species.
