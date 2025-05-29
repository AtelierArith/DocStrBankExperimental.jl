```
get_xl(; basedir=nothing, paramtables = (;setup="params_setup", exper="params_experiment")) 
    → (;abort, xlargs=rslt, fname)
```

Calls the function `NativeFileDialog:` `pick_file(datadir; filterlist)` to select an XLSX.  Passes the file to `read_xl_paramtables` to parse the parameter table(s) If `basedir` not provided, uses the cached value. Caches the selected directory. 

# Keyword arguments

  * `dialogtype`: dialogtype ∈ [:single, :multiple, :folder]
  * `basedir`: The base directory for file selection dialog.

# Returned NamedTuple

  * `abort::Bool`: Dialog cancelled by user
  * `xlargs::NamedTuple`: Tables read into DataFrames - s. [`read_xl_paramtables`](@ref)
  * `fname::String`: Selected XLSX file

Function `get_xl` is public, not exported.
