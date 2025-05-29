```
permissive(tns, dims...)
```

Create an `PermissiveArray` where `permissive(tns, dims...)[i...]` is `missing` if `i[n]` is not in the bounds of `tns` when `dims[n]` is `true`.  This wrapper allows all permissive dimensions to be exempt from dimension checks, and is useful when we need to access an array out of bounds, or for padding. More formally,

```
    permissive(tns, dims...)[i...] =
        if any(n -> dims[n] && !(i[n] in axes(tns)[n]))
            missing
        else
            tns[i...]
        end
```
