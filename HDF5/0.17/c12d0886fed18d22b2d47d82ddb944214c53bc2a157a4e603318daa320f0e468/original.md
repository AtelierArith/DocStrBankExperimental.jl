```
delete_object(parent::Union{File,Group}, path::AbstractString)
```

Delete the object at `parent[path]`.

# Examples

```julia
f = h5open("f.h5", "r+")
delete_object(f, "Group1")
```
