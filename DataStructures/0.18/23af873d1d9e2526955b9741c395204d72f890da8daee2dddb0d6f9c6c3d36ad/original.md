```
nlargest(n, arr; kw...)
```

Return the `n` largest elements of the array `arr`.

Equivalent to:     sort(arr, kw..., rev=true)[1:min(n, end)]

Note that if `arr` contains floats and is free of NaN values, then the following alternative may be used to achieve 2x performance:

```
DataStructures.nextreme(DataStructures.FasterReverse(), n, arr)
```

This faster version is equivalent to:

```
sort(arr, lt = >)[1:min(n, end)]
```
