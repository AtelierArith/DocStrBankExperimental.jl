```julia
struct Plot <: PGFPlotsX.OptionType
```

Corresponds to the `\addplot[3][+]` family of `pgfplot` commands.

Instead of the default constructor, use `Plot([options], data, trailing...)` and similar (`PlotInc`, `Plot3`, `Plot3Inc`) in user code.
