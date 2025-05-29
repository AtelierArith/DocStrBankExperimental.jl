```
textbox(lines::Array, pos::Point=O;
    leading = 12,
    linefunc::Function = (linenumber, linetext, startpos, height) -> (),
    alignment=:left)
```

Draw the strings in the array `lines` vertically downwards. `leading` controls the spacing between each line (default 12), and `alignment` determines the horizontal alignment (default `:left`).

Optionally, before each line, execute the function `linefunc(linenumber, linetext, startpos, height)`.

Returns the position of what would have been the next line.

See also `textwrap()`, which modifies the text so that the lines fit into a specified width.
