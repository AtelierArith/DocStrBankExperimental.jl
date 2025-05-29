```
copy_object(src_parent::Union{File,Group}, src_path::AbstractString, dst_parent::Union{File,Group}, dst_path::AbstractString)
```

`src_parent[src_path]` から `dst_parent[dst_path]` へデータをコピーします。

# 例

```julia
f = h5open("f.h5", "r")
g = h5open("g.h5", "cw")
copy_object(f, "Group1", g, "GroupA")
copy_object(f["Group1"], "data1", g, "DataSet/data_1")
```
