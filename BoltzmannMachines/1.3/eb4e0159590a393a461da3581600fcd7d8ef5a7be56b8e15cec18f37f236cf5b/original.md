```
oneornone_encode(x, categories)
```

Expects a data set `x` containing values 0.0, 1.0, 2.0 ... encoding the categories. Returns a data set that encodes the variables/columns in `x` in multiple columns with only values 0.0 and 1.0, similiar to the one-hot encoding with the deviation that a zero is encoded as all-zeros.

The `categories` can be specified as

  * integer number if all variables have the same number of categories or as
  * integer vector, containing for each variable the number of categories encoded.

See also `oneornone_decode` for the reverse transformation.
