```
create_attribute(parent::Union{File,Object}, name::AbstractString, dtype::Datatype, space::Dataspace)
create_attribute(parent::Union{File,Object}, name::AbstractString, data)
```

Create a new [`Attribute`](@ref) object named `name` on the object `parent`, either by specifying the `Datatype` and `Dataspace` of the attribute, or by providing the data. Note that no data will be written: use [`write_attribute`](@ref) to write the data.
