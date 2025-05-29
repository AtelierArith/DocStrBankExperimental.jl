```
get_variable(o::Union{PyObject, Bool, Array{<:Number}}; 
    name::Union{String, Missing} = missing, 
    scope::String = "")
```

Creates a new variable with initial value `o`. If `name` exists, `get_variable` returns the variable instead of create a new one.
