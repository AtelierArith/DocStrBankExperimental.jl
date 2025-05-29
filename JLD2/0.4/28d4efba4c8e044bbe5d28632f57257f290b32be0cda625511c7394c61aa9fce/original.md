```
load_object(filename)
```

Returns the only available object from the JLD2 file `filename` (The stored object name is inconsequential). If the file contains more than one or no objects, the function throws an `ArgumentError`.

For loading more than one object, use [`@load`](@ref) macro, [`jldopen`](@ref) or the FileIO API.

# Example

To load the only object from the JLD2 file example.jld2:

```julia
hello = "world"
save_object("example.jld2", hello)
hello_loaded = load_object("example.jld2")
```
