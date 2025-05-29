```
read_xl_paramtables(f_src; paramtables=(;setup="params_setup", exper="params_experiment")) 
    → (; df_setup::Union{Nothing, DataFrame}, df_exp::Union{Nothing, DataFrame})
```

Reads the two tables (if not `nothing`) from an XLSX file into corresponding DataFrames and strips comments, if any.  Comment is any row starting with `#` 

# Argument

  * `f_src::String`: File path

# Keyword argument

  * `paramtables=(;setup::Union{Nothing, String}="params_setup", exper::Union{Nothing, String}="params_experiment")`

# Returned NamedTuple

  * `(;df_setup::Union{Nothing, DataFrame}, df_exp::Union{Nothing, DataFrame}`

Function `read_xl_paramtables` is exported.
