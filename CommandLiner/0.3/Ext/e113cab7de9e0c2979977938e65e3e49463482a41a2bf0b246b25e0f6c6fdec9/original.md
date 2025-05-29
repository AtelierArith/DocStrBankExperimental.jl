```
ext(path) -> String or nothing
```

Returns the path extension. Behaves similarly to `Base.splitext(s)[2]`, but does not retain the leading '.'.

Original `splitext`:

  * "myfile.txt"    -> ".txt"
  * "myfile."       -> "."
  * "myfile"        -> ""
  * ".myfile"       -> ""
  * "."             -> ""

New `ext`:

  * "myfile.txt"    -> "txt"
  * "myfile."       -> ""
  * "myfile"        -> nothing
  * ".myfile"       -> nothing
  * "."             -> nothing

See also `exty`, `hasext`.
