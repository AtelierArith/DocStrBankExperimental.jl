```
`@df d x`
```

Convert every symbol in the expression `x` with the respective column in `d` if it exists.

If you want to avoid replacing the symbol, escape it with `^`.

`NA` values are replaced with `NaN` for columns of `Float64` and `""` or `Symbol()` for strings and symbols respectively.

`x` can be either a plot command or a block of plot commands.
