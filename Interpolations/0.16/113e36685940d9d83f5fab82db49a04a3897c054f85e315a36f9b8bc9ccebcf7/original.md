```
itp = interpolate((nodes1, nodes2, ...), A, interpmode)
```

Interpolate an array `A` on a non-uniform but rectangular grid specified by the given `nodes`, in the mode determined by `interpmode`.

`interpmode` may be one of

  * `NoInterp()`
  * `Gridded(Constant())`
  * `Gridded(Linear())`

It may also be a tuple of such values, if you want to use different interpolation schemes along each axis.
