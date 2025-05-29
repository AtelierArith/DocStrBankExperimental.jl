```
merge(db::Surreal; thing::String, data::Union{AbstractDict, Nothing}=nothing)

merge(db::Surreal; thing::String, data::Union{Dict, Nothing}=nothing)
```

merge a record in the database. This function will run the following query in the database: merge `thing` content `data`

# Arguments

  * `thing`: The table or record ID.
  * `data`: The document / record data to merge.

# Examples

```jldoctest

# merge a record with a random ID

julia> person = merge(db, "person")

# merge a record with a specific ID

julia> record = merge(db,"person:tobie", Dict( 	"name"=> "Tobie", 	"settings"=> Dict( 		"active"=> true, 		"marketing"=> true, 		), 	)
