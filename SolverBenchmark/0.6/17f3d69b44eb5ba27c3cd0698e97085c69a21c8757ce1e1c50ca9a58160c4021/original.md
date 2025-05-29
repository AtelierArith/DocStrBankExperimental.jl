```
hl = gradient_highlighter(df, col; cmap=:coolwarm)
```

A PrettyTables highlighter the applies a color gradient to the values in columns given by `cols`.

### Input Arguments

  * `df::DataFrame` dataframe to which the highlighter will be applied;
  * `col::Symbol` a symbol to indicate which column the highlighter will be applied to.

### Keyword Arguments

  * `cmap::Symbol` color scheme to use, from ColorSchemes.
