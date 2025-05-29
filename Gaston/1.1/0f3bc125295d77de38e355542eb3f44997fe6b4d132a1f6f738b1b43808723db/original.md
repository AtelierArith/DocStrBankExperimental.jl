```
save(term, output, [termopts,] [font,] [size,] [linewidth,] [background,] [handle]) -> nothing
```

Save current figure (or figure specified by `handle`) using the specified `term`. Optionally, the font, size, linewidth, and background may be specified as arguments.

Returns `true` in any gnuplot command have been sent else `false`.
