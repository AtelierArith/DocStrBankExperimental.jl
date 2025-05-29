```
set_obs_id_col!(data::DataMatrix, obs_id_col::String; duplicate_obs=:error)
```

Set which column to use as observation IDs. It will be moved to the first column of `data.obs`. The rows of this column in `data.obs` must be unique.

  * `duplicate_obs` - Set to :ignore, :warn or :error to decide what happens if duplicate IDs are found.
