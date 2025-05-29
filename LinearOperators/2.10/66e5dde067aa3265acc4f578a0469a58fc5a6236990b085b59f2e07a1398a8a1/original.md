```
Z = opRestriction(I, ncol)
Z = opRestriction(:, ncol)
```

Creates a LinearOperator restricting a `ncol`-sized vector to indices `I`. The operation `Z * v` is equivalent to `v[I]`. `I` can be `:`.

```
Z = opRestriction(k, ncol)
```

Alias for `opRestriction([k], ncol)`.
