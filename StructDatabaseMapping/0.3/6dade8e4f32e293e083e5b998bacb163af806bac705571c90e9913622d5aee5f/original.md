```
select_all(mapper::DBMapper, T::Type{<:Model}; ; fields::Array{Symbol}=[], kwargs...)
```

Select all the elements that meet a criteria 

# Arguments

  * `mapper::DBMapper`: The database mapper
  * `T::DataType`: Datatype of a registered model we want to search for
  * `kwargs`: criteria we want to search

```
struct Author <: Model ... end
select_all(mapper, Author, age=30)
```
