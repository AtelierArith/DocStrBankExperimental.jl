```
opendb(dbname, [mode])
```

Open a FAME database and return an instance of [`FameDatabase`](@ref) for it.

`dbname` can be a path to a .db file or a string specifying a database over a remote connection in the following format.

```
"[<tcp_port>@]<host> [<username> [<password>] ] <db>"
```

`mode` can be an integer (consult the CHLI help), or a `Symbol`. Valid modes include `:readonly`, `:create`, `:overwrite`, `:update`, `:shared`, `:write`, `:direct_write`.
