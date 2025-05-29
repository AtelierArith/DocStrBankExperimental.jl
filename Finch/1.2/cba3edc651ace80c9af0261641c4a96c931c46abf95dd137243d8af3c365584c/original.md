```
products(tns, dim)
```

Create a `ProductArray` such that

```
    products(tns, dim)[i...] == tns[i[1:dim-1]..., i[dim] * i[dim + 1], i[dim + 2:end]...]
```

This is like [`toeplitz`](@ref) but with times instead of plus.
