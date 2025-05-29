```
toeplitz(tns, dim)
```

Create a `ToeplitzArray` such that

```
    Toeplitz(tns, dim)[i...] == tns[i[1:dim-1]..., i[dim] + i[dim + 1], i[dim + 2:end]...]
```

The ToplitzArray can be thought of as adding a dimension that shifts another dimension of the original tensor.
