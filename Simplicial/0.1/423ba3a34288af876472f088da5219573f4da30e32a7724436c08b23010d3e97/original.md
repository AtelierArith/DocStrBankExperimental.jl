```
sparse_matrix_form(C::CombinatorialCode)
```

A `SparseMatrixCSC` representation of `C` with `Bool` entries; rows as codewords.

Order of returned codewords matches that in `C.words`; assuming no one has been messing around with `C`'s fields, these should be sorted using `lessequal_GrRevLex`.
