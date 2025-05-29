`deletesome!(query, tbl::Table)`

Delete rows that match `query` from the `tbl` Table. Throw an exception if no rows match `query`.

The filtering `query` corresponds to the SQL `WHERE` clause. It can be specified in one of the following forms:

  * `NamedTuple`: specified fields are matched against corresponding table columns, combined with `AND`. Values are converted to corresponding SQL types, see `create_table` for details.
  * `String`: kept as-is.
  * Tuple `(String, args...)`: the `String` is passed to `WHERE` as-is, `args` are SQL statement parameters and can be referred as `?`.
  * Tuple `(String, NamedTuple)`: the `String` is passed to `WHERE` as-is, the `NamedTuple` contains SQL statement parameters that can be referred by name, `:param_name`.
