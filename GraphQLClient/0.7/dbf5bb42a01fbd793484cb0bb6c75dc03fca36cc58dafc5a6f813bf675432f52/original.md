```
create_introspected_struct([client::Client], object_name::AbstractString, fields::AbstractDict)
```

Creates a struct for the object specified and populates its fields with the keys and values of `fields`.

# Examples

```julia
julia> GraphQLClient.create_introspected_struct("ResultObject",Dict(:resultId=>"MyResult", :Score => 1.0))
ResultObject
  Score : 1.0
      resultId : MyResult
```
