```
open(conn::KdbConnectionInfo)::KdbHandle
```

Open a connection to a KDB instance. Returns a `KdbHandle` to the open connection. Also supports `do` syntax:

```
open(conn::KdbConnectionInfo) do h
    execute(h,...)
end
```
