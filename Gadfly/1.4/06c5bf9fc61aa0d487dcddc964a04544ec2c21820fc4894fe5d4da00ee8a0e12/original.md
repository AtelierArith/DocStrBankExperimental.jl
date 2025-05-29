```
plot(data_source::Union{Void, AbstractMatrix, AbstractDataFrame},
     mapping::Dict, elements::ElementOrFunctionOrLayers...) -> Plot
```

The old fashioned (pre-named arguments) version of plot.  This version takes an explicit mapping dictionary, mapping aesthetics symbols to expressions or columns in the data frame.
