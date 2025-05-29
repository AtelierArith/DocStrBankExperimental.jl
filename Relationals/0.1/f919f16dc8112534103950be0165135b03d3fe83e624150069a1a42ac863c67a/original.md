```
@source(fname::String)
@source(c::Expr)
@source(key::QuoteNode, conn::Expr)
@source(key::QuoteNode, fname::String)
```

## Examples

```
# Configure a MySQL data source as the default.
@source DBInterface.connect(
    MySQL.Connection,
    "127.0.0.1", 
    "username", 
    "password";
    db="widgets",
    port=3306,
)

# Configure an SQLite data source only for the Product model.
@source Product "sqlite.db"

```
