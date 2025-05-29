```
collapse(f, A, dim)
```

Reduce `A` towards dimension `dim` using the collapsing function `f` (e.g. `mean`). This means that `f` is applied across all other dimensions of `A`, each of which are subsequently dropped, leaving only the collapsed result of `A` vs. the remaining dimension.
