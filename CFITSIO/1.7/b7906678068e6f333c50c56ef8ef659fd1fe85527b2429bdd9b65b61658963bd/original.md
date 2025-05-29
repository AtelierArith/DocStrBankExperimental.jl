```
fits_read_col(f, colnum, firstrow, firstelem, data)
```

Read data from one column of an ASCII/binary table and convert the data into the specified type `T`.

### Arguments

  * `f::FITSFile`: the file to be read.
  * `colnum::Integer`: the column number, where the value of the first column is `1`.
  * `firstrow::Integer`: the elements to be read start from this row.
  * `firstelem::Integer`: specifies which is the first element to be read, when each cell contains more than one element (i.e., the "repetition count" of the field is greater than one).
  * `data::Array`: at the end of the call, this will be filled with the elements read

from the column. The length of the array gives the overall number of elements.
