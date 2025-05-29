```
clean_table!(mapper::DBMapper, T::Type{<:Model})
```

Remove all elements of the type T.

# Arguments

  * `mapper::DBMapper`: The database mapper
  * `T::Type{<:Model}`: Datatype of a registered model

In cases when possible the structure where those elements are stored (tables in relational case)
