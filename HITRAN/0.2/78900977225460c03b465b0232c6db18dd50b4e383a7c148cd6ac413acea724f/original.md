```
fetch!([db,] name, global_ids, ν_min, ν_max, parameters)
```

Fetches new data from HITRANonline and stores it in the current database in the table given by `name`. If the table with the given parameters already exists, no data download will be initiated.

# Arguments

  * `db`: The database to use for storage (optional)
  * `name`: The table name which can subsequently used as source table for the [`α`](@ref) function
  * `global_ids`: The global isotopologue ids to consider. You can also provide a tuple (or an array of tuples) with `molecule_id`, `local_id` as identifiers
  * `ν_min`: The minimum wavenumber in $cm^{-1}$ to consider
  * `ν_max`: The minimum wavenumber in $cm^{-1}$ to consider
  * `parameters`: A list of parameters to fetch. You can use parameter groups using Symbols as shortcuts, e.g. :standard for all HITRAN standard parameters.
