```
fits_write_col(f, colnum, firstrow, firstelem, data)
```

Write some data in one column of a ASCII/binary table.

If there is no room for the elements, new rows will be created. (It is therefore useless to call [`fits_insert_rows`](@ref) if you only need to *append* elements to the end of a table.)

  * `f::FITSFile`: the file in which data will be written.
  * `colnum::Integer`: the column number, where the value of the first column is `1`.
  * `firstrow::Integer`: the data wil be written from this row onwards.
  * `firstelem::Integer`: specifies the position in the row where the first element will be written.
  * `data::Array`: contains the elements that are to be written to the column of the table.
