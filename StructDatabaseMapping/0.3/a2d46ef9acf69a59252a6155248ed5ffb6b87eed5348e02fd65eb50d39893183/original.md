```
function drop_table!(mapper::DBMapper, T::DataType)
```

Eliminates (when possible) the struct data from the DB

# Arguments

  * `mapper::DBMapper`: The database mapper
  * `T::Type{<:Model}`: Datatype of a registered model
