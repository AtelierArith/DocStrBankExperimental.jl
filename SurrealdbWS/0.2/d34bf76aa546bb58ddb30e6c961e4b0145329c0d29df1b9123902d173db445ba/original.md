```
update(db::Surreal; thing::String, data::Union{Dict, Nothing}=nothing)
```

Updates all records in a table, or a specific record, in the database. This function replaces the current document / record data with the specified data. This function will run the following query in the database: update `thing` content `data`

# Arguments

  * `thing`: The table or record ID.
  * `data`: The document / record data to insert.

# Examples:

```jldoctest
julia> # Update all records in a table
julia> person = update(db, "person")
julia> # Update a record with a specific ID
julia> record = update(db, "person:tobie", Dict(
	"name"=> "Tobie",
	"settings"=> Dict(
	"active"=> true,
	"marketing"=> true,
	),
	))
```
