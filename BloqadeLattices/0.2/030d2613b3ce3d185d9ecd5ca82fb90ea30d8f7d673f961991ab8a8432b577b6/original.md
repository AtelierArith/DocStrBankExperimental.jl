```
random_dropout(sites::AtomList{D, T}, ratio::Real) where {D, T}
random_dropout(ratio)
```

Randomly drop out `ratio * number of sites` atoms from `sites`, where `ratio` ∈ [0, 1].
