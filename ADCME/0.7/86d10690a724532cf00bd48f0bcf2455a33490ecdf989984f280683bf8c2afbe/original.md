```
logging(file::Union{Nothing,String}, o::PyObject...; summarize::Int64 = 3, sep::String = " ")
```

Logging `o` to `file`. This operator must be used with [`bind`](@ref). 
