```
attributes(object::Union{File,Object})
```

The attributes of a file or object: this returns an `Attributes` object, which is `Dict`-like object for accessing the attributes of `object`: `getindex` will return an [`Attribute`](@ref) object, and `setindex!` will call [`write_attribute`](@ref).
