```
Z = opExtension(I, ncol)
Z = opExtension(:, ncol)
```

Creates a LinearOperator extending a vector of size `length(I)` to size `ncol`, where the position of the elements on the new vector are given by the indices `I`. The operation `w = Z * v` is equivalent to `w = zeros(ncol); w[I] = v`.

```
Z = opExtension(k, ncol)
```

Alias for `opExtension([k], ncol)`.
