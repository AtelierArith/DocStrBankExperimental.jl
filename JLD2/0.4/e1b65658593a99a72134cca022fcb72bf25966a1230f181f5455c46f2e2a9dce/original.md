```
save_object(filename, x)
```

Stores an object `x` in a new JLD2 file at `filename`. If a file exists at this path, it will be overwritten.

Since the JLD2 format requires that all objects have a name, the object will be stored as `single_stored_object`. If you want to store more than one object, use [`@save`](@ref) macro, [`jldopen`](@ref) or the FileIO API.

# Example

To save the string `hello` to the JLD2 file example.jld2:

```julia
hello = "world"
save_object("example.jld2", hello)
```
