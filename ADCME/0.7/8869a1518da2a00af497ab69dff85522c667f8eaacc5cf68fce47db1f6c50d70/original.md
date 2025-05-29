```
save(sess::PyObject, file::String, vars::Union{PyObject, Nothing, Array{PyObject}}=nothing, args...; kwargs...)
```

Saves the values of `vars` in the session `sess`. The result is written into `file` as a dictionary. If `vars` is nothing, it saves all the trainable variables. See also [`save`](@ref), [`load`](@ref)
