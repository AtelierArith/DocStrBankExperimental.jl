```
do_read!(obj::FameObject, db::FameDatabase)
```

指定された [`FameObject`](@ref) のデータを、指定された [`FameDatabase`](@ref) から読み込みます。`obj` はその場で変更され、返されます。

[`FameObject`](@ref) は直接作成することもできますし、[`quick_info`](@ref) や [`listdb`](@ref) によって返されることもあります。
