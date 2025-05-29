```
label!(plot, where, value, [color])

label!(plot, where, row, value, [color])
```

This method is responsible for the setting all the textual decorations of a plot.

Note that `where` can be any of: `:tl` (top-left), `:t` (top-center), `:tr` (top-right), `:bl` (bottom-left), `:b` (bottom-center), `:br` (bottom-right), `:l` (left), `:r` (right).

If `where` is either `:l`, or `:r`, then `row` can be between 1 and the number of character rows of the plots canvas.
