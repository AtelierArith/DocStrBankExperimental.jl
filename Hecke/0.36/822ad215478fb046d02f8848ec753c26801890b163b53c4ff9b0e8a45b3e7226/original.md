```
pseudo_hnf(P::PMat)
```

Transforms $P$ into pseudo-Hermite form as defined by Cohen. Essentially the matrix part of $P$ will be upper triangular with some technical normalisation for the off-diagonal elements. This operation preserves the module.

A optional second argument can be specified as a symbols, indicating the desired shape of the echelon form. Possible are `:upperright` (the default) and `:lowerleft`
