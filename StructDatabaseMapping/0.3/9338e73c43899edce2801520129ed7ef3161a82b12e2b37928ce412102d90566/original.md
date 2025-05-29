```
function update!(mapper::DBMapper, elem::T; fields::Array{Symbol}=Symbol[]) where T<:Model
```

Insert the element in the database 

# Arguments

  * `mapper::DBMapper`: The database mapper
  * `elem::T where T<:Model`: Instantied model to insert
  * `fields::Array{Symbol}`: Optional. Array of fields to update.

```
struct Author <: Model ... end
author = Author(name="some name", age=30)
update!(mapper, author)       
update!(mapper, author, fields=[:age])       
```
