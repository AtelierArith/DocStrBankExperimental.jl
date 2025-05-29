```
pdim(DS::AbstractDataSet, model::ModelOrFunction) -> Int
```

Infers the (minimal) number of components that the given function `F` accepts as input by successively testing it on vectors of increasing length.
