```
genus(S::Vector{HermLocalGenus}, signatures) -> HermGenus
```

Given a set of local genus symbols `S`  and a set of signatures `signatures`, return the corresponding global genus symbol `G`. Note that the local genus symbols in `S` must have the same rank which is also, therefore, the rank of `G`.

This constructor requires `S` to be non empty, the signatures to be non negative and that the local invariants respect the product formula for Hilbert symbols.

`signatures` can be a dictionary with keys infinite places and values the corresponding signatures, or a list of tuples $(::InfPlc, ::Int)$.
