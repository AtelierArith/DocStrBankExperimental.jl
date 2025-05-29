```
get_variable(dtype::Type;
shape::Union{Array{<:Integer}, NTuple{N, <:Integer}}, 
name::Union{Missing,String} = missing
scope::String = "")
```

Creates a new variable with initial value `o`. If `name` exists, `get_variable` returns the variable instead of create a new one.
