```
@source(fname::String)
@source(c::Expr)
@source(key::QuoteNode, conn::Expr)
@source(key::QuoteNode, fname::String)
```

## 例

```
# MySQLデータソースをデフォルトとして設定します。
@source DBInterface.connect(
    MySQL.Connection,
    "127.0.0.1", 
    "username", 
    "password";
    db="widgets",
    port=3306,
)

# ProductモデルのためだけにSQLiteデータソースを設定します。
@source Product "sqlite.db"

```
