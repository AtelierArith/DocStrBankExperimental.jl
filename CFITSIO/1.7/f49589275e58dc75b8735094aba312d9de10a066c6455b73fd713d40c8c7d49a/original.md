```
fits_get_coltype(f::FITSFile, colnum::Integer)
```

Provided that the current HDU contains either an ASCII or binary table, return information about the column at position `colnum` (counting from 1).

Return is a tuple containing

  * `typecode`: CFITSIO integer type code of the column.
  * `repcount`: Repetition count for the column.
  * `width`: Width of an individual element.
