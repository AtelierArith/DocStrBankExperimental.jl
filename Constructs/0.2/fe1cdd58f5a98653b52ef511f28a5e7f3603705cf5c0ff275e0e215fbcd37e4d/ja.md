```
RaiseError(error::Exception) -> Construct{Union{}}
RaiseError(message::String) -> Construct{Union{}}
```

特定の `error` または `ErrorException(message)` を、任意のデータのシリアル化またはデシリアル化時に発生させます。
