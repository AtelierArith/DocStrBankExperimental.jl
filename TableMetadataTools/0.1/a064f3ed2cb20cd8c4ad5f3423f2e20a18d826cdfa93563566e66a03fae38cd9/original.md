```
meta2toml(table, style::Bool=true)
```

Store table-level and column-level metadata of `table` in a string using TOML. Non-standard values stored in the metadata are converted as follows:

  * tuples, sets, and arrays to vectors
  * named tuples to dictionaries
  * all other types to `string`.

The `style` keyword argument (`true` by default) determines if metadata style is saved.

The created TOML has three top level keys:

  * `metadata` for table-level metadata key-value pairs;
  * `colmetadata` for column-level metadata; for each column that has metadata an associated value are metadata key-value pairs;
  * `style` storing information about value of `style` keyword argument used.

See also: [`toml2meta!`](@ref)
