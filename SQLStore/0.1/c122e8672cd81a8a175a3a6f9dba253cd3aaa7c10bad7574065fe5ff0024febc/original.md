`create_table(db, name, T::Type{NamedTuple}; [constraints], [keep_compatible=false])`

Create a table with `name` in the database `db` with column specifications derived from the type `T`. Table constraints can be specified by the `constraints` argument. Throws if a table with the same `name` already exists, unless `keep_compatible` is passed. `keep_compatible=true` keeps the existing table if it has a compatible schema.

Supported types:

  * `Int`, `Float64`, `String` are directly stored as corresponding SQL types.
  * `Bool`s stored as `0` and `1` `INTEGER`s.
  * `DateTime`s are stored as `TEXT` with the `'%Y-%m-%d %H:%M:%f'` format.
  * `Dict`s and `Vector`s get translated to their `JSON` representations.
  * Any type can be combined with `Missing` as in `Union{Int, Missing}`. This allows `NULL`s in the corresponding column.
