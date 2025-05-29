```
Tables.columntable(x) => NamedTuple of AbstractVectors
```

Takes any input table source `x` and returns a `NamedTuple` of `AbstractVector`s, also known as a "column table". A "column table" is a kind of default table type of sorts, since it satisfies the Tables.jl column interface naturally.

Note that if `x` is an object in which columns are stored as vectors, the check that these vectors use 1-based indexing is not performed (it should be ensured when `x` is constructed).

Not for use with extremely wide tables with # of columns > 67K; current fundamental compiler limits prevent constructing `NamedTuple`s that large.
