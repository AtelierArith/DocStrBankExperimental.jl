```
DBInterface.execute(conn::DBInterface.Connection, sql::AbstractString, [params]) => DBInterface.Cursor
DBInterface.execute(stmt::DBInterface.Statement, [params]) => DBInterface.Cursor
DBInterface.execute(f::Callable, conn::DBInterface.Connection, sql::AbstractString, [params])
DBInterface.execute(f::Callable, stmt::DBInterface.Statement, [params])
```

Database packages should overload `DBInterface.execute` for a valid, prepared `DBInterface.Statement` subtype (the first method signature is defined in DBInterface.jl using `DBInterface.prepare`), which takes an optional `params` argument, which should be an indexable collection (`Vector` or `Tuple`) for positional parameters, or a `NamedTuple` for named parameters. Alternatively, the parameters could be specified as keyword agruments of `DBInterface.execute`.

`DBInterface.execute` should return a valid `DBInterface.Cursor` object, which is any iterator of "rows", which themselves must be property-accessible (i.e. implement `propertynames` and `getproperty` for value access by name), and indexable (i.e. implement `length` and `getindex` for value access by index). These "result" objects do not need to subtype `DBInterface.Cursor` explicitly as long as they satisfy the interface. For DDL/DML SQL statements, which typically do not return results, an iterator is still expected to be returned that just iterates `nothing`, i.e. an "empty" iterator.

Note that `DBInterface.execute` returns **a single** `DBInterface.Cursor`, which represents a single resultset from the database. For use-cases involving multiple result-sets from a single query, see `DBInterface.executemultiple`.

If function `f` is provided, `DBInterface.execute` will return the result of applying `f` to the `DBInterface.Cursor` object and close the prepared statement upon exit.
