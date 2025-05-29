```
initialize(::Type{<:MaternCorrelationStructure}, data::IDFdata)
```

Initialize a vector of parameters for the MaternCorrelationStructure adapted to the data. The initialization is done by fitting the correlation function to the Kendall's Tau (measure of correlation) associated to each pair of durations.
