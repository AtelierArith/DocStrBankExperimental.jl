```
tabletype(d::DTable)
```

Provides the type of the underlying table partition. Uses the cached tabletype if available.

In case the tabletype cannot be obtained the default return value is `NamedTuple`.
