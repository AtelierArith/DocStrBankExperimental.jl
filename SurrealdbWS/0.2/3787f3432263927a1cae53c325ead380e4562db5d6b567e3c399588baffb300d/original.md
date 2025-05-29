```
delete(db::Surreal; thing::String)
```

Deletes all records in a table, or a specific record, from the database. This function will run the following query in the database: delete * from `thing`

# Arguments

`thing`: The table name or a record ID to delete.

# Examples

julia> # Delete all records from a table julia> delete(db, "person") julia> # Delete a specific record from a table julia> delete(db, "person:h5wxrf2ewk8xjxosxtyc")
