```
residue_identification(s, f, poles, weight) -> residues, d, h
```

Stage 2 of the Vector Fitting. This should be called separately for each column of `f` and `weight` when `ndims(f) == 2`.

See also [`vector_fitting`](@ref), [`pole_identification`](@ref).
