```
swizzle(tns, dims)
```

Create a `SwizzleArray` to transpose any tensor `tns` such that

```
    swizzle(tns, dims)[i...] == tns[i[dims]]
```
