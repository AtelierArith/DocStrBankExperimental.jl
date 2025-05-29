```
select(db::Surreal; thing::String)
```

Selects all records in a table (or other entity), or a specific record, in the database. This function will run the following query in the database: select * from `thing`

# Arguments

```
`thing`: The table or record ID to select.
```

# Returns:

```
The records.
```

# Examples

```jldoctest
# Select all records from a table (or other entity)
julia> people = select(db, "person")
# Select a specific record from a table (or other entity)
julia> person = select(db, "person:h5wxrf2ewk8xjxosxtyc")
```
