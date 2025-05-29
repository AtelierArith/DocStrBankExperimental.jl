```
Repeat(; [row::Vector], [column::Vector], [layer::Vector])
Repeat(field::Vector{SymbolOrString}; columns::Int=nothing)
```

Creates a `RepeatSpec` for a repeat specification. [](https://vega.github.io/vega-lite/docs/repeat.html). A `field` can be passed as a positional argument, or must be passed in the `row`/`column/layer` keyword argument.

# Examples

```
Repeat([:Horsepower, :Miles_per_Gallon, :Acceleration], columns=2)
Repeat(column=[:distance, :delay, :time])
```
