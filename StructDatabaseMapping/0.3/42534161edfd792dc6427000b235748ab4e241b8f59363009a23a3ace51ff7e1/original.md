```
function delete!(mapper::DBMapper, T::Type{<:Model}; kwargs...)
```

Remove elements from the database

# Arguments

  * `mapper::DBMapper`: The database mapper
  * `T::DataType`: Datatype of a registered model we want to delete
  * `kwargs`: fields we want to search for existence.

```
struct Author <: Model ... end
delete!(mapper, Author, name="some name", age=30)
```
