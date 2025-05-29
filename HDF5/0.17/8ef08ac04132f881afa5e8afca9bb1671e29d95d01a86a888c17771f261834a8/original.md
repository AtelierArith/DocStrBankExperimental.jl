```
attrs(object::Union{File,Group,Dataset,Datatype})
```

The attributes dictionary of `object`. Returns an `AttributeDict`, a `Dict`-like object for accessing the attributes of `object`.

```julia
attrs(object)["name"] = value  # create/overwrite an attribute
attr = attrs(object)["name"]   # read an attribute
delete!(attrs(object), "name") # delete an attribute
keys(attrs(object))            # list the attribute names
```
