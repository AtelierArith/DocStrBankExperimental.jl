```
Database(filename::Union{Missing, String} = missing; 
    commit_after_execute::Bool = true)
```

Creates a database from `filename`. If `filename` is not provided, an in-memory database is created.  If `commit_after_execute` is false, no commit operation is performed after each [`execute`](@ref).

  * do block syntax:

```julia
Database() do db
    execute(db, "create table mytable (a real, b real)")
end
```

The database is automatically closed after execution. Therefore, if execute is a query operation,  users need to store the results in a global variable. 

  * Query meta information

```julia
keys(db) # all tables 
keys(db, "mytable") # all column names in `db.mytable` 
```
