```
tabletype!(gd::GDTable)
```

Provides the type of the underlying table partition and caches it in `gd`.

In case the tabletype cannot be obtained the default return value is `NamedTuple`.
