```
function select_one(mapper::DBMapper, T::Type{<:Model}; kwargs...)
```

Select one element from the database

# Arguments

  * `mapper::DBMapper`: The database mapper
  * `T::DataType`: Datatype of a registered model we want to select
  * `kwargs`: fields we want to search for. The param pk cand be used as generic way

to identify the primary key of the struct

```
struct Author <: Model ... end
select_one(mapper, Author, name="Borges")       
```
