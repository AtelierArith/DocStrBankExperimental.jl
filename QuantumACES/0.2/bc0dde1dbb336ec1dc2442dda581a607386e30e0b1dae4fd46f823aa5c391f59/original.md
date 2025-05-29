```
get_augmented_tuple_set_data(tuple_set_data::TupleSetData, repeat_points::Integer; initial_shrink_factor::Real = 2^(repeat_points - 1))
```

Returns an augmented version of the tuple set data `tuple_set_data`, where each of the repetition numbers is augmented to have `repeat_points` total repetition numbers, spaced logarithmically between the repetition number and the repetition number shrunk by a factor of `initial_shrink_factor`.
