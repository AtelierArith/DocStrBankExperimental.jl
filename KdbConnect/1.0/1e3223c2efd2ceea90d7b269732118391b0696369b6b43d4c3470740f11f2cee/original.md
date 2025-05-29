```
execute(hobj::KdbHandle, query::AbstractString, args...)
execute(conn::KdbConnectionInfo, query::AbstractString, args...)
```

Execute a query on a KDB instance via an open connection handle `hobj::KdbHandle`. If the first argument is a `KdbConnectionInfo`, a temporary handle will be opened and closed automatically. A query consists of a string and optional `args` which are sent to the KDB instance.

Examples:

```
    execute(hobj,"1+1")
    execute(hobj,"{x+y}", π-3, 3)
    execute(hobj,"{0N!x}","Hello from KDB!")
    execute(conn, "([] w:10?(0nj,til 3) ;x:10?1f ; y:10?(12;1b;`foo;"bar") ; z:10?`3)")
```
