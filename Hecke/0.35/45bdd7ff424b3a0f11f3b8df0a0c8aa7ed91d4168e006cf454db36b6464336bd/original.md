```
relative_residue_field(O::RelNumFieldOrder, P::RelNumFieldOrderIdeal) -> RelFinField, Map
```

Given a maximal order `O` in a relative number field $E/K$ and a prime ideal `P` of `O`, return the residue field $O/P$ seen as an extension of the (relative) residue field of a maximal order in `K` at $minimum(P)$.

Note that if `K` is a relative number field, the latter will also be seen as a relative residue field.
