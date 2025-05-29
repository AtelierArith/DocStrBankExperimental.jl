```
modelcols(t::AbstractTerm, data)
```

Create a numerical "model columns" representation of data based on an `AbstractTerm`.  `data` can either be a whole table (a property-accessible collection of iterable columns or iterable collection of property-accessible rows, as defined by [Tables.jl](https://github.com/JuliaData/Tables.jl) or a single row (in the form of a `NamedTuple` of scalar values).  Tables will be converted to a `NamedTuple` of `Vectors` (e.g., a `Tables.ColumnTable`).
