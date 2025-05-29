```
printmatrix(mat [, Val(F), colnames])
```

Display a matrix in full while controlling the formatting of each value and optionally showing the column names.

  * `Val(F)` - display each number in the given format `F`. The format is in the form of a decimal point number where the whole part indicates the total width and the fractional part indicates the number of digits printed after the decimal point. Default is `Val(12.7)`
  * `colnames` - a list of names to display in the first row. The names are displayed as given, possibly with padding to match the width given in the `Val` argument. If any names are longer than that, they will not be truncated and so the display will not be aligned properly. Sorry about that!
