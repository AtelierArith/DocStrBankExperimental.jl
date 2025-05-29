```
textlines(s::T where T <: AbstractString, width::Real;
     rightgutter=5)
```

Split the text in `s` into lines up to `width` units wide (in the current font).

Returns an array of strings. Use `textwrap` to draw an array of strings.

TODO: A `rightgutter` optional keyword adds some padding to the right hand side of the column. This appears to be needed sometimes -— perhaps the algorithm needs improving to take account of the interaction of `textextents` and spaces?
