```
execute(db::Database, sql::String, args...)
```

Executes the SQL statement `sql` in `db`. Users can also use the do block syntax. 

```julia
execute(db) do 
    "create table mytable (a real, b real)"
end
```

`execute` can also be used to insert a batch of records

```julia
t1 = rand(10)
t2 = rand(10)
param = collect(zip(t1, t2))
execute(db, "INSERT TO mytable VALUES (?,?)", param)
```

or 

```julia
execute(db, "INSERT TO mytable VALUES (?,?)", t1, t2)
```
