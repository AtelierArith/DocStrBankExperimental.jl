```
read_attribute(parent::Union{File,Group,Dataset,Datatype}, name::AbstractString)
```

Read the value of the named attribute on the parent object.

# Example

```julia-repl
julia> HDF5.read_attribute(g, "time")
2.45
```
