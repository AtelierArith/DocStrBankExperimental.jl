```
function delete!(mapper::DBMapper, T::Type{<:Model}; kwargs...)
```

Remove elements from the database

# Arguments

  * `mapper::DBMapper`: The database mapper
  * `elem<:Model`: Element to delete

The element needs a valid identifier.

```
struct Author <: Model ... end
delete!(mapper, Author(id=valid_id, name="some name", age=30))
```
