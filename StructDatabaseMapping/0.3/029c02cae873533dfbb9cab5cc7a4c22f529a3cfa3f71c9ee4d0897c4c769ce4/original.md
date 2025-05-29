```
function exists(mapper::DBMapper, elem::T) where T<:Model
```

Return wether the element exists in the database

# Arguments

  * `mapper::DBMapper`: The database mapper
  * `elem<:Model`: Element to determine its existence

```
struct Author <: Model ... end
exists(mapper, Author(name="some name", age=30))
```
