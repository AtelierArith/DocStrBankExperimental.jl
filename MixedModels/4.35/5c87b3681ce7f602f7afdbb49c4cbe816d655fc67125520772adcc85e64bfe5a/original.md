```
RaggedArray{T,I}
```

A "ragged" array structure consisting of values and indices

# Fields

  * `vals`: a `Vector{T}` containing the values
  * `inds`: a `Vector{I}` containing the indices

For this application a `RaggedArray` is used only in its `sum!` method.
