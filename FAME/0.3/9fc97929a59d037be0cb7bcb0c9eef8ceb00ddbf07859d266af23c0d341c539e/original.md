```
do_write(obj::FameObject, db::FameDatabase)
```

Write the given [`FameObject`](@ref) to the given [`FameDatabase`](@ref). If an object by the same name already exists, it is deleted before the new object is written.
