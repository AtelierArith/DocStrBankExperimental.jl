```
get_row_idxs(table, conditions) -> row_idxs
```

Returns row indices of the passed-in table that correspond to `conditions`, where `conditions` can be:

  * `::Colon` - all rows
  * `::Int64` - a single row
  * `::AbstractVector{Int64}` - a list of rows
  * `p::Pair` - returns a Vector containing the index of each row for which `comparison(p[2], typeof(row[p[1]]))(row[p[1]])` is true.  See [`comparison`](@ref)
  * `pairs`, an iterator of `Pair`s - returns a Vector containing the indices which satisfy all the pairs as above.

Some possible pairs to filter by:

  * `:nation => "narnia"`: checks if the `nation` column is equal to the string "narnia"
  * `:emis_co2 => >=(0.1)`: checks if the `emis_co2` column is greater than or equal to 0.1
  * `:age => (2,10)`: checks if the `age` column is between 2, and 10, inclusive.  To be exclusive, use different values like (2.0001, 9.99999) for clarity
  * `:state => in(("alabama", "arkansas"))`: checks if the `state` column is either "alabama" or "arkansas"

Used in [`get_table`](@ref) and [`get_table_row_idxs`](@ref).
