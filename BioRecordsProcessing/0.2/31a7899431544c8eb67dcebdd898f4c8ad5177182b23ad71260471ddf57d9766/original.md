```julia
Collect(T::DataType; paired=false)
```

Write the output of the processing function into an vector in memory. The type of output has to be provided. For paired files the option paired need to be set to `true`, the output will then consists of a vector of tuples.
