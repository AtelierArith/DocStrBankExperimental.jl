```
Material(path::String) -> Union{Material, Vector{Material}
```

Creates a material from the given path in the refractive index database. This method will throw an `ArgumentError` if the given path does not correspond to a material in the database.

# Arguments

  * `path::String` : The path to the material given in the format "<shelf>/<book>/<page>"

# Returns

  * `Union{Material, Vector{Material}` : The material object(s) created from the given path. The method returns a vector of material objects if the page at the given path contains multiple material datasets.
