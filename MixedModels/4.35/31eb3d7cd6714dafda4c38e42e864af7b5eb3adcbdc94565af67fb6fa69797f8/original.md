```
BlockedSparse{Tv,S,P}
```

A `SparseMatrixCSC` whose nonzeros form blocks of rows or columns or both.

# Members

  * `cscmat`: `SparseMatrixCSC{Tv, Int32}` representation for general calculations
  * `nzasmat`: nonzeros of `cscmat` as a dense matrix
  * `colblkptr`: pattern of blocks of columns

The only time these are created are as products of `ReMat`s.
