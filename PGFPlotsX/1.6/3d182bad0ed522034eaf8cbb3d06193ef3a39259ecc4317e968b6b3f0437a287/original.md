```
GroupPlot([options], contents...)
```

A group plot, using the `groupplots` library of PGFPlots.

The `contents` after the global options are processed as follows:

1. [`Options`](@ref) (ie from `@pgf {}`) will emit a `\nextgroupplot` with the given options,
2. `nothing` is emitted as a `\nextgroupplot[group/empty plot]`,
3. [`Axis`](@ref), [`SemiLogXAxis`](@ref), [`SemiLogYAxis`](@ref) and [`LogLogAxis`](@ref) are emitted as `\nextgroupplot[options...]`, followed by the contents,
4. other values, eg `Plot` are emitted using [`print_tex`](@ref).
