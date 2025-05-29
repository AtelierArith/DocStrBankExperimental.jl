```
do_read!(obj::FameObject, db::FameDatabase)
```

Read data for the given [`FameObject`](@ref) from the given [`FameDatabase`](@ref). `obj` is modified in place and returned.

A [`FameObject`](@ref) can be created directly, or it could be returned by [`quick_info`](@ref) or [`listdb`](@ref).
