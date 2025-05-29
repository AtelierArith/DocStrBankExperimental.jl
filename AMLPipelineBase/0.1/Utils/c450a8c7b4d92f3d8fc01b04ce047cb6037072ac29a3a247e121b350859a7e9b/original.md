```
infer_eltype(vector::Vector)
```

Returns element type of vector unless it is Any. If Any, returns the most specific type that can be inferred from the vector elements.

  * `vector`: vector to infer element type on

Returns: inferred element type
