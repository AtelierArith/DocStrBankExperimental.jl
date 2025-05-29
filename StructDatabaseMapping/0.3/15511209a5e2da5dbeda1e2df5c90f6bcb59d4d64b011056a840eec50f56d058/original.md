```
function register!(mapper::DBMapper, d::Type{T}; table_name::String="") where T <: Model
```

Register an element of type T into the mapper. A Table type is created for the given Model and is stored in the dabase. This function must be called for each type you want to use with this library.
