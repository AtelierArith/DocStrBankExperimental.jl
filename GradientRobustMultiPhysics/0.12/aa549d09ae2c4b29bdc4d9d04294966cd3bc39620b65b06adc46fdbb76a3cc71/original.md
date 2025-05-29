```
function DataFunction(c::Array{<:Real,1}; name = "constant user data", quadorder::Int = 0)
```

Directly generates a DataFunction from a given array c, i.e. a DataFunction that is constant and has no dependencies on x or t.
