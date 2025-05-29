```
filterobs(f, data)
```

Return a subset of data container `data` including all indices `i` for which `f(getobs(data, i)) === true`.

```julia
data = 1:10
numobs(data) == 10
fdata = filterobs(>(5), data)
numobs(fdata) == 5
```
