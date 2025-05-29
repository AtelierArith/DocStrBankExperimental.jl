```
Base.convert(
    ::Type{SparseMatrixCSC{Tv,Ti}},
    A::MutableSparseMatrixCSC{Tv,Ti,I},
) where {Tv,Ti,I}
```

Converts `A` to a `SparseMatrixCSC`. Note that the field `A.nzval` is **not copied** so if `A` is modified after the call of this function, it can still affect the value returned. Moreover, if `I` is `OneBasedIndexing`, `colptr` and `rowval` are not copied either, that is, the conversion is allocation-free.
