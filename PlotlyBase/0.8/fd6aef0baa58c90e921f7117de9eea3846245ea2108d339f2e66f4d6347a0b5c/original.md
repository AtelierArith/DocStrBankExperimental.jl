```julia
Plot(x, y; ...)
Plot(x, y, l; kind, config, kwargs...)

```

Build a plot of with one trace of type `kind`and set `x` to x and `y` to y. All keyword arguments are passed directly as keyword arguments to the constructed trace.

**NOTE**: If `y` is a matrix, one trace is constructed for each column of `y`

**NOTE**: If `x` and `y` are both matrices, they must have the same number of columns (say `N`). Then `N` traces are constructed, where the `i`th column of `x` is paired with the `i`th column of `y`.
