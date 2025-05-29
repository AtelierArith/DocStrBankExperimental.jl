```
copy_object(src_obj::Object, dst_parent::Union{File,Group}, dst_path::AbstractString)
```

# Examples

```julia
copy_object(f["Group1"], g, "GroupA")
copy_object(f["Group1/data1"], g, "DataSet/data_1")
```
