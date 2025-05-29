```
TupleSetData
```

Data parameterising a tuple set.

# Fields

  * `tuple_set::Vector{Vector{Int}}`: The main tuple set, whose tuples are not repeated.
  * `repeat_tuple_set::Vector{Vector{Int}}`: The repeat tuple set, whose tuples are repeated according to the `repeat_numbers`.
  * `repeat_numbers::Vector{Int}`: The number of repetitions for tuples in the repeat tuple set `repeat_tuple_set`.
  * `repeat_indices::Vector{Tuple{Int, Int}}`: Indexes pairs (`repeat_tuple`, `repeat_number`) from (`repeat_tuple_set`, `repeat_numbers`) such that the repeated tuple set consists of `repeat_tuple` repeated `repeat_number` times for all indexed pairs.
