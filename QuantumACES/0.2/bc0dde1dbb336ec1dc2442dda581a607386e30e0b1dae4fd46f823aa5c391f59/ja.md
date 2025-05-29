```
get_augmented_tuple_set_data(tuple_set_data::TupleSetData, repeat_points::Integer; initial_shrink_factor::Real = 2^(repeat_points - 1))
```

`tuple_set_data`の拡張バージョンを返します。ここで、各繰り返し数は、繰り返し数と`initial_shrink_factor`で縮小された繰り返し数の間を対数的に間隔を空けて、合計`repeat_points`の繰り返し数を持つように拡張されます。
