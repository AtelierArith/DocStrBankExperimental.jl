function exists(mapper::DBMapper, T::Type{T}; kwargs...) where T <: Model

Return wether the element exists in the database

# Arguments

  * `mapper::DBMapper`: The database mapper
  * `T::DataType`: Datatype of a registered model we want to know their existence
  * `kwargs`: fields we want to search for existence. The param pk cand be used as generic way

to identify the primary key of the struct

```
struct Author <: Model ... end
exists(mapper, Author, name="some name", age=30)
```
