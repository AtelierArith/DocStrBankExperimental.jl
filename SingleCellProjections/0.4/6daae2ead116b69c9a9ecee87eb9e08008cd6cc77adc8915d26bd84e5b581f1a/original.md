```
set_var_id_col!(data::DataMatrix, var_id_col::String; duplicate_var=:error)
```

Set which column to use as variable IDs. It will be moved to the first column of `data.var`. The rows of this column in `data.var` must be unique.

  * `duplicate_var` - Set to :ignore, :warn or :error to decide what happens if duplicate IDs are found.
