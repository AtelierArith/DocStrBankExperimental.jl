```
insert(db::Surreal; thing::String, data::Union{Dict, Nothing}=nothing)
```

insert a record in the database. This function will run the following query in the database: insert `thing` content `data`

# Arguments

  * `thing`: The table or record ID.
  * `data`: The document / record data to insert.

# Examples

```jldoctest

# insert a record with a random ID

julia> person = insert(db, "person")

# insert a record with a specific ID

julia> record = insert(db,"person:tobie", Dict( 	"name"=> "Tobie", 	"settings"=> Dict( 		"active"=> true, 		"marketing"=> true, 		), 	)
