```
pseudo_hnf_with_transform(P::PMat)
```

Transforms $P$ into pseudo-Hermite form as defined by Cohen. Essentially the matrix part of $P$ will be upper triangular with some technical normalisation for the off-diagonal elements. This operation preserves the module. The used transformation is returned as a second return value.

A optional second argument can be specified as a symbol, indicating the desired shape of the echelon form. Possible are `:upperright` (the default) and `:lowerleft`
