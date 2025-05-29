```
nlines = count_display_lines(io, ds)
```

Count the number of lines needed to display the contents of `io` in a terminal of [`displaysize`](@ref) `ds`. This handles "line wrap" as well as newlines.
