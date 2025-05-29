```
JuMP.set_name(pref::ScalarParameterRef, name::String)
```

Extend the `JuMP.set_name` function to accomodate infinite parameters. Set a new  base name to be associated with `pref`.

**Example**

```julia-repl
julia> set_name(t, "time")

julia> name(t)
"time"
```
