```
get_script_path(p)
```

Accept a Julia script (with user defined functions) as full path for user functions of just file name for examples delivered with this package. If the file not found, return the path to the empty file "dummy.jl". If `p` is empty string, return path to "Examples-UserFn.jl", which in turn includes some example scripts. Set the global `scriptexists` to `true` if everything OK.

# Examples

```julia-repl

julia> include(get_script_path(raw"C:\Users\eben\Desktop\Julia\my_functions.jl"))
julia> server_0mq4lv((;foo=foo, bar, baz))
```
