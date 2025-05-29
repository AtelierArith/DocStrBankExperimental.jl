```
create(db::Surreal; thing::String, data::Union{Dict, Nothing}=nothing)
```

Create a record in the database. This function will run the following query in the database: create `thing` content `data`

# Arguments

  * `thing`: The table or record ID.
  * `data`: The document / record data to insert.

# Examples

```jldoctest

# Create a record with a random ID

julia> person = create(db, "person")

# Create a record with a specific ID

julia> record = create(db,"person:tobie", Dict( 	"name"=> "Tobie", 	"settings"=> Dict( 		"active"=> true, 		"marketing"=> true, 		), 	)
