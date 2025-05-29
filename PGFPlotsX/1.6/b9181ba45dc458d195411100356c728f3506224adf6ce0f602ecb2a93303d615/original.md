```
Plot([options::Options], data, trailing...)
```

A plot with the given `data` (eg [`Coordinates`](@ref), [`Table`](@ref), [`Expression`](@ref), …) and `options`, which is empty by default.

Corresponds to `\addplot` in PGFPlots.

`trailing` can be used to provide *trailing path commands* (eg `\closedcycle`, see the PGFPlots manual), which are emitted using `print_tex`, before the terminating `;`.
