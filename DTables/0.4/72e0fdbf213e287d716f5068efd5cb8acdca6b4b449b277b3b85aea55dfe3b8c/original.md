```
tabletype!(d::DTable)
```

Provides the type of the underlying table partition and caches it in `d`.

In case the tabletype cannot be obtained the default return value is `NamedTuple`.
