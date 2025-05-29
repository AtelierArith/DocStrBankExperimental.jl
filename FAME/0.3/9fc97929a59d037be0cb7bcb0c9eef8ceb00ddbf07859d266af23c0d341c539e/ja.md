```
do_write(obj::FameObject, db::FameDatabase)
```

指定された [`FameObject`](@ref) を指定された [`FameDatabase`](@ref) に書き込みます。同じ名前のオブジェクトがすでに存在する場合は、新しいオブジェクトが書き込まれる前に削除されます。
