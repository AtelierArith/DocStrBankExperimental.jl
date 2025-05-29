```
IndirectArray(index, values)
```

creates an array `A` where the values are looked up in the value table, `values`, using the `index`.  Concretely, `A[i...] = values[index[i...]]`.

`values` can be an `AbstractVector` (useful when the values in `index` are contiguous) or an `AbstractDict` (useful when they are not). When there are not very many such distinct values, "frozen" LittleDicts from [OrderedCollections](https://github.com/JuliaCollections/OrderedCollections.jl) are recommended for performance.
