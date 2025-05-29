```
offline_run!(model, t::Union{Real, Function}; kwargs...)
```

Do the same as [`run!`](@ref), but instead of collecting all the data into an in-memory dataframe, write the output to a file after collecting data `writing_interval` times and empty the dataframe after each write. Useful when the amount of collected data is expected to exceed the memory available during execution.

## Keywords

  * `backend=:csv` : backend to use for writing data. Currently supported backends: `:csv`, `:arrow`.
  * `adata_filename="adata.$backend"` : a file to write agent data on. Appends to the file if it already exists, otherwise creates the file.
  * `mdata_filename="mdata.$backend"`: a file to write the model data on. Appends to the file if it already exists, otherwise creates the file.
  * `writing_interval=1` : write to file every `writing_interval` times data collection is triggered (which is set by the `when` and `when_model` keywords).
  * All other keywords are propagated to [`run!`](@ref).
