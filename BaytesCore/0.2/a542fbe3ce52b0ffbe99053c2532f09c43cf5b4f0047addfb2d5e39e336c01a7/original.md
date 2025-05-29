```julia
struct ArrayConfig{K, T<:BaytesCore.DataSorting}
```

Array configuration struct.

Checks if data is propagated row or column wise.

# Fields

  * `size::NTuple{K, Int64} where K`: Dimension of data.
  * `sorted::BaytesCore.DataSorting`: Boolean if data is sorted by row
