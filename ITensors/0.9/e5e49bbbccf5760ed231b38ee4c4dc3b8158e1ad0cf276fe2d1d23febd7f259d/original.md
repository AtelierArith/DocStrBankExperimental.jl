```
dag(T::ITensor; allow_alias = true)
```

Complex conjugate the elements of the ITensor `T` and dagger the indices.

By default, an alias of the ITensor is returned (i.e. the output ITensor may share data with the input ITensor). If `allow_alias = false`, an alias is never returned.
