```
get_data(;dialogtype, filterlist="", datadir=nothing) 
    → (; abort::Bool, datafiles)
```

Calls the function `NativeFileDialog:` `pick_file(datadir; filterlist)` or `pick_multi_file(datadir; filterlist)`.  If `datadir` not provided, uses the cached value. Caches the selected directory. Returns file or folder or multiple files.

# Keyword arguments

  * `dialogtype`: dialogtype ∈ [:single, :multiple, :folder]
  * `datadir`: The base directory for file selection dialog.
  * `filterlist`: Will be passed to `pick_file` / `pick_multi_file` function.

# Throws

  * On unknown value of `dialogtype`

Function `get_data` is public, not exported.
