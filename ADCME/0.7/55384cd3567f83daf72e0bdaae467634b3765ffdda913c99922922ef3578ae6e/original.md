```
load(sess::PyObject, file::String, vars::Union{PyObject, Nothing, Array{PyObject}}=nothing, args...; kwargs...)
```

Loads the values of variables to the session `sess` from the file `file`. If `vars` is nothing, it loads values to all the trainable variables. See also [`save`](@ref), [`load`](@ref)
