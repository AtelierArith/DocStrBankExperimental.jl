```
xicor(X, Y; rank=tiedrank, noties=false)
```

Computes the asymmetric ξ correlation coefficient sbetween two vectors `X` and `Y`. `rank` species how the rank is computed, default uses `denserank`. If there are no ties in `Y`, `noties` can be set to `true`, which speeds up computation.

`ξ` is an alias for this function.
