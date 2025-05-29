```
delete_object(parent::Union{File,Group}, path::AbstractString)
```

`parent[path]`のオブジェクトを削除します。

# 例

```julia
f = h5open("f.h5", "r+")
delete_object(f, "Group1")
```
