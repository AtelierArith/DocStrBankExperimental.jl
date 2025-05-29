```
vproduct(x, y) -> z
```

yields the element-wise multiplication of `x` by `y`.  To avoid allocating the result, the destination array `dst` can be specified with the in-place version of the method:

```
vproduct!(dst, [sel,] x, y) -> dst
```

which overwrites `dst` with the elementwise multiplication of `x` by `y`. Optional argument `sel` is a selection of indices to which apply the operation.
