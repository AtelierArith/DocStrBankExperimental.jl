```
fits_insert_rows(f::FITSFile, firstrow::Integer, nrows::Integer)
```

Insert a number of rows equal to `nrows` after the row number `firstrow`.

The elements in each row are initialized to their default value: you can modify them later using [`fits_write_col`](@ref).

Since the first row is at position 1, in order to insert rows *before* the first one `firstrow` must be equal to zero.
